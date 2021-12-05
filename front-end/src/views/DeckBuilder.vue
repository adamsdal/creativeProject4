<template>
<div class="deckbuilder">
  <h1>Build Your Deck!</h1>
    <div class="heading">
      <div class="circle">1</div>
      <h2>Add a Card</h2>
    </div>
    <div class="add">
      <div class="form">
        <input v-model="name" placeholder="Name">
        <p></p>
        <input v-model="characteristicName" placeholder="Type">
        <input v-model="characteristicValue" placeholder="Value">
        <button @click="addCharacteristic">+ Characteristic</button>
        <p></p>
        <input type="file" name="photo" @change="fileChanged">
        <button @click="upload">Upload</button>
      </div>
      <div class="upload" v-if="addItem">
        <h2>{{addItem.title}}</h2>
        <img :src="addItem.path" />
      </div>
    </div>
    <hr>
	<div class="heading">
      <div class="circle">2</div>
      <h2>Edit/Delete a Card</h2>
    </div>
    <div class="edit">
      <div class="form">
        <input v-model="findName" placeholder="Search">
        <div class="suggestions" v-if="suggestions.length > 0">
          <div class="suggestion" v-for="s in suggestions" :key="s.id" @click="selectItem(s)">{{s.name}}
          </div>
        </div>
      </div>
      <div class="upload" v-if="findItem">
        <input v-model="findItem.name">
        <p></p>
        <div v-for="(value, name) in findItem.characteristics" :key="name">
          <label>{{name}}: <input v-model="findItem.characteristics[name]"></label>
        </div>
        <p></p>
        <img :src="findItem.path" />
      </div>
      <div class="actions" v-if="findItem">
        <button @click="deleteItem(findItem)">Delete</button>
		    <button @click="editItem(findItem)">Edit</button>
      </div>
    </div>

</div>
</template>



<script>
import axios from 'axios';
export default {
  name: 'DeckBuilder',
  data() {
    return {
      name: "",
      characteristicName: "",
      characteristicValue: "",
      file: null,
      addItem: null,
      items: [],
      findName: "",
      findItem: null,
		  characteristics: {},
      newCharacteristicID: 0,
    }
  },
  methods: {
    addCharacteristic() {
      if (this.characteristicName === "" || this.characteristicValue === "") {
        alert("Characteristic is missing a name/value");
        return;
      }
      this.characteristics[this.characteristicName] = this.characteristicValue;
    },
    fileChanged(event) {
      this.file = event.target.files[0]
    },
	async upload() {
      try {
        const formData = new FormData();
        formData.append('photo', this.file, this.file.name)
        let r1 = await axios.post('/api/photos', formData);
        let r2 = await axios.post('/api/items', {
          name: this.name,
		      characteristics: this.characteristics,
          path: r1.data.path
        });
        this.addItem = r2.data;
      } catch (error) {
        console.log(error);
      }
    },
	async getItems() {
		try {
			let response = await axios.get("/api/items");
			this.items = response.data;
			return true;
		} catch (error) {
			console.log(error);
		}
	},
	selectItem(item) {
      this.findName = "";
      this.findItem = item;
    },
	async deleteItem(item) {
      try {
        await axios.delete("/api/items/" + item._id);
        this.findItem = null;
        this.getItems();
        return true;
      } catch (error) {
        console.log(error);
      }
    },
	async editItem(item) {
      try {
        await axios.put("/api/items/" + item._id, {
          name: this.findItem.name,
		      characteristics: this.findItem.characteristics,
        });
        this.findItem = null;
        this.getItems();
		    console.log(this.items);
        return true;
      } catch (error) {
        console.log(error);
      }
    },


  },
  created() {
    this.getItems();
  },
  computed: {
    suggestions() {
      let items = this.items.filter(item => item.name.toLowerCase().startsWith(this.findName.toLowerCase()));
      return items.sort((a, b) => a.name > b.name);
    }
  },



}
</script>



<style scoped>
.image h2 {
  font-style: italic;
  font-size: 1em;
}

.heading {
  display: flex;
  margin-bottom: 20px;
  margin-top: 20px;
}

.heading h2 {
  margin-top: 8px;
  margin-left: 10px;
}

.add,
.edit {
  display: flex;
}

.circle {
  border-radius: 50%;
  width: 28px;
  height: 28px;
  padding: 4px;
  background: rgb(43, 138, 19);
  color: rgb(255, 255, 255);
  text-align: center
}

/* Form */
input,
textarea,
select,
button {
  font-family: 'Montserrat', sans-serif;
  font-size: 1em;
}

.form {
  margin-right: 50px;
}

/* Uploaded images */
.upload h2 {
  margin: 0px;
}

.upload img {
  max-width: 300px;
}

/* Suggestions */
.suggestions {
  width: 200px;
  border: 1px solid #ccc;
}

.suggestion {
  min-height: 20px;
}

.suggestion:hover {
  background-color: #5BDEFF;
  color: #fff;
}

.deck-builder {

}
</style>