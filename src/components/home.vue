<template>
  <body class="container">
    <div>
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
        <h1 class="h1">Mariano Puchetta</h1>
        <h2>Developer</h2>
      </header>
      <section>
        <h3>
          Github repositories listed by api.github.com
        </h3>
        <div class="grid-container">
          <div v-for="(repo, index) in repos" :key="index" id="mydiv">
            <b-card-group deck>
              <b-card
                class="b-card"
                border-variant="primary"
                :header="repo.name"
                :footer="repo.language"
                header-bg-variant="primary"
                header-text-variant="white"
                align="center"
              >
                <b-card-text class="description"> {{ repo.description }}</b-card-text>
               

                <div class="links">
                  <a
                    :href="repo.html_url"
                    target="_blank"
                    :title="repo.html_url"
                    >GitHub repo</a
                  >
                  <a
                    v-if="repo.homepage != ''"
                    :href="repo.homepage"
                    target="_blank"
                    :title="repo.homepage"
                    >Website</a
                  >
                </div>
              </b-card>
            </b-card-group>
          </div>
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
import { AXIOS } from "./http-common";

export default {
  name: "home",
  data() {
    return {
      repos: [],
    };
  },

  methods: {
    retrieveGitPost() {
      AXIOS.get(
        "https://api.github.com/users/marianopuchetta/repos?sort=created_at"
      )
        .then((response) => {
          this.repos = response.data;
          console.log(this.repos);
        })
        /*eslint-disable*/
        .catch((e) => {
          console.log(e);
        });
    },
  },
  mounted() {
    this.retrieveGitPost();
  },
};
</script>

<style scoped >
@import url("https://fonts.googleapis.com/css2?family=Ranchers&family=Roboto:wght@500&display=swap");
@import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css");

.container {
  display: flex;
  flex-direction: column;
  text-align: center;
}
nav {
  display: flex;
}
.h1 {
  margin-top: 2.5vh;
  font-size: 6em;
  text-shadow: -1px -1px 1px white, 1px 0px 10px rgb(105, 100, 100);
}
h2 {
  margin-right: 5vh;
  display: flex;
  justify-content: flex-end;
  text-shadow: -1px -1px 1px white, 1px -1px 4px rgb(105, 100, 100);
  font-size: 2em;
  font-weight: 600;
}
h3 {
  margin-bottom: 5vh;
  margin-top: 5vh;
  text-shadow: -1px -1px 1px white, 1px -1px 5px rgb(105, 100, 100);
}
.grid-container {
  display: grid;
  grid-template-columns: 57vh 57vh 57vh;
  grid-template-rows: 35vh;
  grid-gap: 5vh;
  column-gap: 3vh;
  padding: 1vh;
}

a:link {
  text-decoration: none;
}

/* li {
  color: white;
  text-shadow: 2px 2px 0 rgba(45, 10, 240, 0.4),
    2px -2px 0 rgba(45, 10, 240, 0.4), -2px 2px 0 rgba(45, 10, 240, 0.4),
    -2px -2px 0 rgba(45, 10, 240, 0.4), 2px 0px 0 rgba(45, 10, 240, 0.4),
    0px 2px 0 rgba(45, 10, 240, 0.4), -2px 0px 0 rgba(45, 10, 240, 0.4),
    0px -2px 0 rgba(45, 10, 240, 0.4);
} */

footer {
  margin-top: 5vh;
}
nav .fa,
footer .fa {
  font-size: 2.5em;
  padding: 2vh;
  width: 200px;
  display: inline-block;
  width: 1em;
  text-shadow: -1px -1px 1px white, 1px -1px 5px rgb(105, 100, 100);
  color: black;
}
.fa:hover {
  font-size: 3em;
}
.links {
  font-size: 0.9em;
  display: flex;
  justify-content: space-around;
}
.links > a:hover {
  font-size: 1.1em;
}

@media only screen and (max-width: 768px) {
  .grid-container {
    grid-template-columns: 45vh 45vh;
    grid-template-rows: 45vh;
  }
  header > h1 {
    font-size: 4em;
  }
}
@media only screen and (max-width: 576px) {
 
  body {
    display: flex;
    justify-content: center;
    width: 100%;
  }

  .h1 {
    font-size: 3em;
  }
  h2 {
    font-size: 1.1em;
    margin-right: 0vh;
  }
  h3 {
    font-size: .9em;
  }
  .grid-container {
    display: flex;
    flex-flow: column nowrap;
  }
  footer {
    margin-top: 5vh;
  }
  nav .fa,
  footer .fa {
    font-size: 1.5em;
    padding: 1vh;
  }

  .links {
    font-size: 0.7em;
    display: flex;
    justify-content: space-around;
  }
  .b-card{
    font-size: .85em;
    
  }
  .description{
    font-size: .8em;
  }
}
</style>

