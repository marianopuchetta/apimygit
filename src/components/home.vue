<template>
   <body class="container">
     <div >
     <header>
       <h1 id="h1">Mariano Puchetta</h1>
    <h3 class="text-center" >List my GitHub Repositories using api.github.com</h3>
    
     </header>
    <section class="grid-container">

       <div v-for="(repo,index) in repos" :key="index" >
      <a :title="repo.description" :href="repo.html_url" target="_blank">
       <b-badge variant="success" class="badge"> <li>{{repo.name}}</li></b-badge>
        {{repo.hmtl_url}}
      </a>
    </div>
    
    </section>
<footer>
   <div>
      <a href="https://github.com/marianopuchetta" target="_blank">
        <i class="fa fa-github" style="font-size:48px;"></i>
      </a>
      <a href="https://linkedin.com/in/marianopuchetta" target="_blank">
        <i class="fa fa-linkedin" style="font-size:48px;"></i>
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
      repos: []
    }
  },

  methods: {
    retrieveGitPost () {
      AXIOS.get('https://api.github.com/users/marianopuchetta/repos')
        .then(response => {
          this.repos = response.data
        })
        /*eslint-disable*/
        .catch(e => {
          console.log(e);
        });
    }
  },
  mounted() {
    this.retrieveGitPost();
  }
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Ranchers&family=Roboto:wght@500&display=swap');
@import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css");
body{
  /* height:100%; */
  font-family: 'Roboto', sans-serif;
  display: flex;
  flex-direction: column;
}
.container {
  display: flex;
  flex-direction: column;
  text-align: center;
  background: rgba(182, 169, 230, 0.5);
}
header{
  padding:3vh;
  margin:5vh;
}
 h1 {
  text-shadow: 3px 3px 3px rgb(80, 80, 80);
  text-shadow: -1px -1px 1px white;
  text-shadow: 1px -1px -1px white;
} 
 h3 {
  text-shadow: 3px 3px 3px rgb(80, 80, 80);
  text-shadow: -1px -1px 1px white;
  text-shadow: 1px -1px -1px white;
} 
.grid-container {
  display: grid;
  grid-template-columns: auto auto auto;
  grid-template-rows: 10vh 10vh;
  grid-gap: 1vh;
  padding: 5vh;
}
.badge{
  margin-bottom:5vh;
  padding:2vh;
  color:black;
}
a:link {
  text-decoration: none;
}
li {
  list-style: none;
  font-size: 1.7em;
  text-shadow: -1px -1px 3px rgb(248, 243, 243);
  text-shadow: 3px -1px -1px rgb(245, 240, 240);
}
li:hover {
  font-size: 1.8em;
  text-shadow: -1px -1px 3px red;
  text-shadow: 3px -1px -1px red;
}
.a.title {
  visibility: hidden;
}
footer{
  margin-top: 5vh;
}
.fa {
  padding: 4px;
  width: 200px;
  display: inline-block;
  width: 1em;
  text-shadow: -1px -1px 1px white;
  text-shadow: 1px -1px -1px white;
}
.fa::after {
  color: black;
}
.fa::before {
  color: black;
}
@media only screen and (max-width: 1024px){
   .grid-container {
  grid-template-columns: auto auto;
  grid-template-rows: 10vh 10vh;
  padding: 5vh;
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
 h1 {
 
} 
 h3 {
 font-size:1.5em;
}
  .grid-container {
  grid-template-columns: auto;
  grid-template-rows: 10vh 10vh;
  padding: 5vh;
  }
  li {
  list-style: none;
  font-size: 1.2em;
}
li:hover {
  font-size: 1.4em;
}
}
</style>
