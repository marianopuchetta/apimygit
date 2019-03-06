<template>
   <div class="container">
    <h1 id="h1">Mariano Puchetta</h1>
    <h3 class="text-center" id="h2">List my GitHub Repositories using api.github.com</h3>

    <div v-for="(repo,index) in repos" :key="index">
      <a :title="repo.description" :href="repo.html_url" target="_blank">
        <li>{{repo.name}}</li>
        {{repo.hmtl_url}}
      </a>
    </div>
    <div id="panelMedia">
      <a href="https://github.com/marianopuchetta" target="_blank">
        <i class="fa fa-github" style="font-size:48px;"></i>
      </a>
      <a href="https://linkedin.com/in/marianopuchetta" target="_blank">
        <i class="fa fa-linkedin" style="font-size:48px;"></i>
      </a>
    </div>
  </div>
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
@import url("https://fonts.googleapis.com/css?family=Acme|Pacifico");
@import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css");
.fa {
  padding: 4px;
  width: 200px;
  display: inline-block;
  width: 1.28571429em;
  text-shadow: -1px -1px 1px white;
  text-shadow: 1px -1px -1px white;
}
.fa::after {
  color: black;
}
.fa::before {
  color: black;
}

#h2 {
  font-family: "Pacifico";
  text-shadow: 3px 3px 3px rgb(80, 80, 80);
  text-shadow: -1px -1px 1px white;
  text-shadow: 1px -1px -1px white;
}
#h1 {
  font-family: "Acme";
  text-shadow: 3px 3px 3px rgb(80, 80, 80);
  text-shadow: -1px -1px 1px white;
  text-shadow: 1px -1px -1px white;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  background: rgba(153, 149, 149, 0.6);
}
a:link {
  text-decoration: none;
}
li {
  list-style: none;
  font-family: "Acme", cursive;
  font-size: 20px;
  text-shadow: -1px -1px 3px white;
  text-shadow: 3px -1px -1px white;
}
li:hover {
  font-size: 28px;
  text-shadow: -1px -1px 3px red;
  text-shadow: 3px -1px -1px red;
}
.a.title {
  visibility: hidden;
}
</style>
