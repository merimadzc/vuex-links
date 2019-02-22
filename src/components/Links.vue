<template>
  <div id="links">
    <!-- Links with Vuex -->
    <div class="left">
      <form v-on:submit.prevent="addLinks()">
        <input type="url" v-model="newLink" placeholder="https://" required="required" />
      </form>
      <ul v-if="countLinks >= 1">
        <li v-for="(link, index) in links" v-bind:key="index" v-on:dblclick="removeLinks" title="Remove">
          {{ link }}
        	<a v-bind:href="link" target="_blank">
            <i class="fa fa-external-link" title="Open"></i>
          </a>
        </li>
      </ul>
	</div>
	<div class="right">
	  <h3 v-if="countLinks >= 1">There are currently {{ countLinks }} 
	  	<p v-if="countLinks == 1">link</p>
	  	<p v-else>links</p>.
	  </h3>
      <button v-on:click="removeAllLinks" v-if="countLinks >= 1">Remove all links</button>
      <h3>{{ msg }}</h3>
	</div>
  </div>
</template>

<script>
import { mapState, mapGetters, mapMutations, mapActions } from 'vuex'
export default {
  name: 'Links',
  data() {
  	return {
  	  newLink: '',
  	  msg: '',
  	  count: 'link',
  	}
  },
  computed: {
  	...mapState([
  	  'links', 'link',
  	]),
  	...mapGetters([
  	  'countLinks'
  	]),
  },
  methods: {
  	...mapMutations([
  	  'ADD_LINKS',
  	]),
  	...mapActions([
  	  'removeLink', 'removeAll',
  	]),
  	addLinks() {
  	  this.ADD_LINKS(this.newLink)
  	  this.newLink = ''
  	  this.msg = ''
  	},
  	removeLinks(link) {
  	  this.removeLink(link)
  	},
  	removeAllLinks() {
  	  this.removeAll().then(() => {
  	  	this.msg = 'Links have been removed.'
  	  })
  	},
  }
}
</script>

<style type="text/css">
#links {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 10%;
  margin: 40px;
}
ul {
  margin-top: 0;
  padding: 20px;
  text-align: center;
  background: rgba(0, 0, 0, 0.1);
  border-bottom-right-radius: 50px;
  max-height: 50vh;
  width: calc(100% - 40px);
  overflow-y: auto;
  overflow-x: hidden;
  list-style: none;
}
ul li {
 cursor: pointer;
 font-size: 1.1em;
 color: rgba(0, 0, 0, 0.5);
 text-decoration: none;
}
ul li:hover {
 text-decoration-line: line-through; 
 text-decoration-color: red;
}
ul li a {
  color: rgba(0, 0, 0, 0.5);
  padding-left: 10px;
}
ul li a:hover {
  color: rgba(0, 0, 0, 0.8);
}
form input {
  border: none;
  padding: 20px;
  width: calc(100% - 40px);
  box-shadow: 0 5px 5px lightgrey;
  outline: none;
  margin-bottom: 0;
  font-size: 1em;
}
.right {
  padding: 50px;
  background: rgba(0,0,0, 0.8);
  border-top-left-radius: 50px;
  box-shadow: -15px 20px 15px rgba(0, 0, 0, 0.3);  
  text-align: center;
  max-height: 38vh;
}
h3 {
  font-size: 2em;
  color: rgba(255,255,255, 0.7);
}
p {
  display: inline-block;
  margin: 0;
  padding: 0;
}
button {
  width: auto;
  height: 60px;
  background: rgba(255, 255, 255, 0.9);
  text-transform: uppercase;
  font-size: 1.5em;
  font-weight: bold;
  border: 2px solid transparent;
  border-bottom-left-radius: 10px;
  border-top-right-radius: 10px;
  cursor: pointer;
  outline: none;
}
button:hover {
  background: transparent;
  border: 2px solid rgba(255, 255, 255, 0.9);
  color: rgba(255, 255, 255, 0.9);
}
</style>