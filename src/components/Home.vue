<template>
  <div id="home">
  	<h1>{{ title }}</h1>
  	<div class="made-with-love">
      <h4>Made with <i class="fa fa-heart-o" aria-hidden="true"></i> by Merima 
      	<a href="https://github.com/merimadzc" target="_blank">
          <i class="fa fa-github"></i>
      	</a>
      </h4>
    </div>
    <Links></Links>
  </div>
</template>

<script>
import Links from './Links.vue'
import { mapState } from 'vuex'

export default {
  name: 'Home',
  components: {
    Links
  },
  computed: {
  	...mapState([
  	  'title'
  	]),
  }
}
</script>

<style type="text/css">
h1 {
  text-align: center;
  font-family: 'Rubik Mono One', sans-serif;
  font-size: 3em;
}

/* Made with <3 Style*/
.made-with-love {
  color: rgba(0,0,0,0.6);
  font-family: 'Parisienne', cursive;
  text-align: center;
  font-size: 1.3em;
}
.made-with-love i {
  color: red;
}
.made-with-love i:hover {
  color: red;
}
</style>