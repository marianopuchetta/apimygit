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
      <a class="download_cv" id="download_cv"  href="https://drive.google.com/file/d/1oRxIUPQrJQ5Lqaqolve3Gu42-1F1GsvK/view?usp=sharing" target="_blank" download>CV</a>

        <h3>
          Github repositories listed by api.github.com
        </h3>
        <div class="grid-container">
          <div v-for="(repo, index) in repos" :key="index" id="mydiv">
            <b-card-group deck>
              <b-card
                class="b-card"
                border-variant="primary"
                :header="repo.name.toUpperCase()"
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
      AXIOS.get(
        'https://api.github.com/users/marianopuchetta/repos?sort=created_at'
      )
        .then((response) => {
          this.repos = response.data
        })
        /*eslint-disable*/
        .catch((e) => {
          console.log(e);
        });
    },
       onScroll(e) {
      let elem = document.getElementById("download_cv")

        if (window.scrollY !== 0) {
          elem.style.top = "88vh";
        } else {
          elem.style.top = "2vh";
        }
      
    }
 
   },

 created:  function () {
      this.retrieveGitPost();
     window.addEventListener("scroll", this.onScroll);
  

  },
   destroyed: function () {
    window.removeEventListener("scroll", this.onScroll);
  },
};
</script>

<style scoped >
@import url("https://fonts.googleapis.com/css2?family=Ranchers&family=Roboto:wght@500&display=swap");
@import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css");
img{
  width: 500px;
  height: 500px;
}
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
  font-weight: 700;
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
  grid-template-columns: 53vh 53vh 53vh;
  grid-template-rows: 43vh;
  grid-gap: 5vh;
  column-gap: 3vh;
  padding: 1vh;
}
.download_cv{
    display: block; /* Hidden by default */
    position: fixed; /* Fixed/sticky position */
    top: 1.5vh; /* Place the button at the bottom of the page */
    right: 13vh; /* Place the button 30px from the right */
    z-index: 99; /* Make sure it does not overlap */
    background-color : rgba(255, 0, 0, 0.8); /* Set a background color */
    color: white; /* Text color */
    cursor: pointer; /* Add a mouse pointer on hover */
    padding: 2vh; /* Some padding */
    border-radius: 50%; /* Rounded corners */
    border:2px solid white;
    font-size: 1.4em; /* Increase font size */
    font-weight: 900;
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
 .description{
    font-size: .9em;
    font-weight: 600;
  }

@media only screen and (max-width: 1024px) {
  .grid-container {
    grid-template-columns: auto auto;
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
    font-size: 4em;
    font-weight: 700;
  }
  h2 {
    font-size: 1.1em;
    margin-right: 0vh;
    font-weight: 700;
  }
  h3 {
    font-size: 1em;
    font-weight: 700;
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
    font-size: 0.8em;
    display: flex;
    justify-content: space-around;
    font-weight: 600;
  }
  .b-card{
    font-size: .85em;
   font-weight: 500;
    
  }
  .description{
    font-size: 1em;
    font-weight: 500;
  }
  .download_cv{
      display: block; /* Hidden by default */
    position: fixed; /* Fixed/sticky position */
    top: 1vh; /* Place the button at the bottom of the page */
    right: 2vh; /* Place the button 30px from the right */
    padding: 2vh; /* Some padding */
    font-size: 1.4em; /* Increase font size */
    font-weight: 900;
}
}
</style>

