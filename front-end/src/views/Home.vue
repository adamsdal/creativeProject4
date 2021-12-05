<template>
<div>
	<div class="holderContainer">
		<h1>Fantasy Deck Builder of Destiny 9000</h1>
		<p class="subParagraph">Have you ever wanted to have the most amazing deck building experience this world can offer?
			 Have you ever considered buying green beans from the store? Since I already know the answer to both of these questions 
			 is an obvious yes, I'll just introduce to you the solution to one of your yearnings.... THE FANTASY DECK BUILDER 9000
		</p>
		<div class="spacer"></div>
		<h2>Build cross-universe teams</h2>
		<p class="subParagraph">We allow you to build your team across mutliple universes of characters</p>
		<div class="spacer"></div>
		<h2>Customize your cards</h2>
		<p class="subParagraph">The ultimate flexibility is allowed in making your deck combinations as you can make your own categories, make your own stats, and uploading your own pictures</p>
		<div class="spacer"></div>
		<h2>View your ultimate team</h2>
		<p class="subParagraph">After you build your custom team you can view them all together to see the team of ages you've built</p>
		<div class="spacer"></div>
		<img src="../../public/team.png">
		<div class="spacer"></div>
	</div>
</div>
</template>

<script>
export default {
  name: 'Home',
    data() {
    return {

    }
  }

  
}
</script>


<style scoped>
h1 {
  font-weight: bold;
  color: #202020;
  font-size: 40px;
}

h2 {
	font-weight: bold;
  color: #202020;
  font-size: 35px;
}

.spacer {
	height:25px;
	width:100%;
}

.subParagraph {
	margin-left: 12px;
	color: #404040;
}

.holderLeft {
	width: 65%;
	min-width: 400px;
}

.holderRight {
	width: 65%;
	min-width: 400px;
}

.holderContainer {
	width: 90%;
}

/* Masonry */
*,
*:before,
*:after {
  box-sizing: inherit;
}

.image-gallery {
  column-gap: 1.5em;
}

.image {
  margin: 0 0 1.5em;
  display: inline-block;
  width: 100%;
}

.image img {
  width: 100%;
}

/* Masonry on large screens */
@media only screen and (min-width: 1024px) {
  .image-gallery {
    column-count: 4;
  }
}

/* Masonry on medium-sized screens */
@media only screen and (max-width: 1023px) and (min-width: 768px) {
  .image-gallery {
    column-count: 3;
  }
}

/* Masonry on small screens */
@media only screen and (max-width: 767px) and (min-width: 540px) {
  .image-gallery {
    column-count: 2;
  }
}
</style>

