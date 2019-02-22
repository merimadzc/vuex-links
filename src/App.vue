<template>
  <div id="app">
    <Home></Home>
  </div>
</template>

<script>
import Home from './components/Home.vue'

export default {
  name: 'app',
  components: {
    Home
  }
}
</script>
<style type="text/css">
@import url('https://fonts.googleapis.com/css?family=Parisienne|Rubik+Mono+One');
body {
  background: rgba(200, 200, 200, 0.1);
}

/* Media Query */
@media only screen and (max-width: 800px) { 
  h1 {
  	font-size: 2em;
  }
  #links {
	grid-template-columns: 1fr;
	grid-gap: 5%;
	margin: 20px 20px 60px 20px;
  }
  h3 {
  	font-size: 1.2em;
  }
  button {
  	height: 50px;
  	font-size: 1.1em;
  }
}
</style>
