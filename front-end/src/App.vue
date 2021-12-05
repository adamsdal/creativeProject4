<template>
<div id="app">
	<nav class="navbar navbar-expand-lg navbar-light bg-dark">
	<router-link style="width: 10%" to="/">
      <div class="logo">
        <img style="width: 100%" src="/deckbuild.png">
      </div>
    </router-link>
		<button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
		<span class="navbar-toggler-icon"></span>
		</button>

		<div class="collapse navbar-collapse" id="navbarSupportedContent">
		<ul class="navbar-nav mr-auto">
			<li class="nav-item">
			<div class="headerLink">
				<router-link class="nav-link" style="color:white;" to="/">Home</router-link>
			</div>
			</li>
			<li class="nav-item">
				<router-link class="nav-link" style="color:white;" to="/deckBuilder">Deck Builder</router-link>
			</li>
			<li class="nav-item">
				<router-link class="nav-link" style="color:white;" to="/viewer">Deck Viewer</router-link>
			</li>
		</ul>
		</div>
	</nav>
  <div class="content">
    <router-view />
  </div>
  <div class="footer">
    <a href="https://github.com/adamsdal/creativeProject4">Wanna view that freaking sweet git repository? Yeah baby! Click it up right here! You've viewed Dallan and Dallin's project. </a>
  </div>
</div>
</template>

<style>
html {
  box-sizing: border-box;
}

.headerLink {
	display:flex;
	
}

body {
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  background: #fff;
  padding: 0px;
  margin: 0px;
}

/* Header */
.header {
  display: flex;
  padding: 10px 100px 0px 100px;
  background-color: #5BDEFF;
  color: #1C454F;
}

.title {
  margin-top: 5px;
}

.title h1 {
  font-size: 30px;
}

.content {
  padding: 20px 100px;
  min-height: 500px;
}

/* Footer */
.footer {
  height: 50px;
  padding: 20px 100px 0px 100px;
  background: #e3e3e3;
  font-size: 12px;
}

.footer a {
  color: #000;
}

h1 {
  font-size: 20px;
}

h2 {
  font-size: 14px;
}
</style>
