<template>
   <body class="container">
     <div >
     <header>
       <nav>
           <div>
      <a href="mailto:marianopuchetta@hotmail.com" target="_blank">
        <i class="fa fa-envelope"></i>
      </a>
      <a href="https://github.com/marianopuchetta" target="_blank">
        <i class="fa fa-github"></i>
      </a>
      <a href="https://linkedin.com/in/marianopuchetta" target="_blank">
        <i class="fa fa-linkedin"></i>
      </a>
    </div>
       </nav>
       <h1 id="h1">Mariano Puchetta</h1>
       <h3 class="text-center" >these are my Github repositories using api.github.com</h3>
     </header>
    <section class="grid-container">
       <div v-for="(repo,index) in repos" :key="index" id="mydiv" > 
      <!-- <a :title="repo.description" :href="repo.html_url" target="_blank"> -->
       <b-dropdown variant="outline-success" dropup  class="button"   id="button" dropdown-toggle="dropdown" :text="repo.name" no-caret>
       <b-dropdown-item-button  class="drop_item"> <a :href="repo.html_url" target="_blank" :title="repo.html_url"><i class="fa fa-github"></i></a></b-dropdown-item-button>
       <b-dropdown-item-button  class="drop_item"><a  v-if="repo.homepage != null" :href="repo.homepage" target="_blank" :title="repo.homepage"><i class="fa fa-chrome"></i></a></b-dropdown-item-button>
       </b-dropdown>
      <!-- </a> -->
       
    </div>
    
    </section>
<footer>
   <div>
      <a href="mailto:marianopuchetta@hotmail.com" target="_blank">
        <i class="fa fa-envelope"></i>
      </a>
      <a href="https://github.com/marianopuchetta" target="_blank">
        <i class="fa fa-github"></i>
      </a>
      <a href="https://linkedin.com/in/marianopuchetta" target="_blank">
        <i class="fa fa-linkedin"></i>
      </a>
    </div>
</footer>
  </div>
   </body>
</template>
<script>
import { AXIOS } from './http-common'

export default {
  name: 'home',
  data () {
    return {
      repos: [],  
    }
  },

  methods: {
    retrieveGitPost () {
      AXIOS.get('https://api.github.com/users/marianopuchetta/repos?per_page=100')
        .then(response => {
          this.repos = response.data
          console.log(this.repos)
        })
        /*eslint-disable*/
        .catch(e => {
          console.log(e);
        });
    },
  },
  mounted() {
    this.retrieveGitPost();
  }
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->


<style scoped >
@import url('https://fonts.googleapis.com/css2?family=Ranchers&family=Roboto:wght@500&display=swap');
@import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css");
body{
  margin-top:2vh;
  font-family: 'Roboto', sans-serif;
  display: flex;
  flex-direction: column;
}
.container {
  display: flex;
  flex-direction: column;
  text-align: center;
  background: rgba(182, 169, 230, 0.4);
}
.grid-container {
  display: grid;
  grid-template-columns: auto auto auto;
  grid-template-rows: 10vh 10vh;
  grid-gap: 7vh;
  column-gap:3vh;
  padding: 1vh;
}
header>h1{
   padding:3vh;
   margin-top:4vh;
   margin-bottom: 3vh;
   font-family: 'Ranchers', cursive;
   font-size:6em;
} 
 h3 {
   font-family: 'Ranchers', cursive;
   margin-bottom: 7vh;
}

.drop_item .fa-chrome {
  font-size: 1.8em;
}
.drop_item .fa-github {
  font-size: 2em;
}

a:link {
  text-decoration: none;
}
li {
  list-style: none;
  font-size: 1.3em;
  color:white;
  background-color: transparent;
}
li:hover {
  font-size: 1.5em;
}
h1,h3,li{
    color:white;
    text-shadow: 2px 2px 0 rgba(45, 10, 240, 0.4), 
             2px -2px 0 rgba(45, 10, 240, 0.4),
            -2px 2px 0 rgba(45, 10, 240, 0.4),
            -2px -2px 0 rgba(45, 10, 240, 0.4), 
             2px 0px 0 rgba(45, 10, 240, 0.4), 
             0px 2px 0 rgba(45, 10, 240, 0.4),
            -2px 0px 0 rgba(45, 10, 240, 0.4),
             0px -2px 0 rgba(45, 10, 240, 0.4);
}
.a.title {
  visibility: hidden;
}
footer{
  margin-top: 5vh;
}
nav  .fa, footer  .fa {
  font-size: 3em;
  padding: 2vh;
  width: 200px;
  display: inline-block;
  width: 1em;
  text-shadow: -1px -1px 1px white;
  text-shadow: 1px -1px -1px white;
}
nav  .fa, footer , .fa {
  color: black;
}
nav  .fa, footer  .fa, .circle {
  color: black;
}
@media only screen and (max-width: 1024px){
   .grid-container {
  grid-template-columns: auto auto;
  grid-template-rows: 10vh 10vh;
  padding: 5vh;
  }
  header>h1{
 font-size:4em;
} 
}
@media only screen and (max-width: 768px) {
  body{
    display:flex;
    justify-content: center;
  }
  header{
  padding:3vh;
  margin:3vh;
}
 header>h1{
 font-size:3.5em;
} 
 h3 {
 font-size:1.5em;
}
  .grid-container {
  grid-template-columns: auto;
  grid-template-rows:5vh;
  grid-gap: 6vh;
  padding: 1vh;
  }
  li {
  list-style: none;
  font-size: 1.6rem;
}
li:hover {
  font-size: 1.7em;
}
}
</style>
<style >
.dropdown-menu{
  background-color: transparent !important;
  border:none;
  transform: translate3d(2vh, -45px, 0px) !important;
}
.dropdown-item{
  background-color: transparent !important;
  border:none;
}
.dropdown-menu.show {
    display: flex;
   padding:0;
   flex-flow: row nowrap;
}
@media only screen and (max-width: 768px){
  .dropdown-menu{
  transform: translate3d(2vh, -55px, 0px) !important;
}
}
</style>
