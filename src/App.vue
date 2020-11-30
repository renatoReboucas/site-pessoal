<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <div class="text-center container-picture">
          <img
            :src="profile.avatar_url"
            class="picture rounded mx-auto d-block"
            alt="autor-picture"
          />
        </div>
      </div>
    </div>

    <div class="row">
      <div class="col">
        <div class="container-title">
          <h1 class="title">Renato Rebouças</h1>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <div class="content-bio">
          <p>
            Renato é uma amante de tecnologia desde se da por gente, quando
            criança vivia na frente de computadores e consoles. Mas na
            adolescência descobriu realmente sua paixão por códigos. Ao ver que
            o que o limitava era ele mesmo, buscou estudar e se dedicar cada vez
            mais na área. Uma das coisas que mais o motivou foram as pessoas
            duvidarem de sua capacidade na área e a dois anos atua como
            programador web
          </p>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col content-bio">
        <p>Tenho conhecimento em HTML, Javascript, Node, PHP, Laravel, Mysql, Vue, React e CSS. </p>
      </div>
    </div>

     <!-- <div class="row">
      <div class="col content-bio">
        <button>Baixar Curriculo</button>
      </div>
    </div> -->

    <div class="row">
      <div class="col">
        <div class="social-content">
          <a
            href="http://github.com/renatoReboucas"
            target="_blank"
            rel="noopener noreferrer"
            class="icons-social"
          >
            <i class="fab fa-github"></i> @renatoReboucas
          </a>
          <a
            href="mailto:renato190698@gmail.com"
            target="_blank"
            rel="noopener noreferrer"
            class="icons-social"
          >
            <i class="far fa-envelope"></i> renato190698@gmail.com
          </a>
          <span class="icons-social">
            <i class="fas fa-map-marker-alt"></i> São Paulo, Brasil
          </span>
        </div>
      </div>
    </div>

    <div class="row">
      <div class="col content-social-media">
        <a
          href="https://twitter.com/https_zero6"
          target="_blank"
          rel="noopener noreferrer"
          class="social-media"
        >
          <i class="fab fa-twitter"></i>
        </a>
        <a
          href="https://www.linkedin.com/in/renato-rebou%C3%A7as-9bb008132/"
          target="_blank"
          rel="noopener noreferrer"
          class="social-media"
        >
          <i class="fab fa-linkedin"></i>
        </a>
        <a
          href="https://dev.to/renato_zero6"
          target="_blank"
          rel="noopener noreferrer"
          class="social-media"
        >
          <i class="fab fa-dev"></i>
        </a>
      </div>
    </div>

  <!-- <div class="row">
    <div class="col title-git">
      <h3>Meus Projetos</h3>
      <p>Esses são os repositórios do <strong>github</strong> que eu construi.</p>
    </div>
  </div>
  <div class="row">
    <div class="col">
      <div class="box">
        <p>api-lumen</p>
      </div>
    </div>
  </div> -->

  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'
import "bootstrap/dist/css/bootstrap.min.css";

export default {
  // name: 'App',
  // components: {
  //   HelloWorld
  // }
  data() {
    return {
      profile: null,
      repos: null,
      error: null,
    };
  },
  mounted() {
    this.getProfile()
    this.getReposOne()
  },
  methods: {
    getProfile() {
      axios
        .get("https://api.github.com/users/renatoReboucas")
        .then((res) => {
          // console.log(res.data);
          this.profile = res.data;
        })
        .catch((error) => {
          console.log("Deu ruim:", error);
          this.error = "Deu ruim";
        });
    },
    getReposOne() {
      const repo =  axios.get("https://api.github.com/repos/renatoReboucas/api-lumen")
      this.repos = repo.data
    },

  },

  // end export
};
</script>

<style>
* {
  box-sizing: border-box;
  background: #191d27 !important;
  color: #fff !important;
  font-family: "Roboto", sans-serif;
}
#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
img {
  width: 24px;
}
body,
ul,
li,
h1,
h2,
p {
  padding: 0px;
  margin: 0px;
}
ul {
  list-style: none;
}
a {
  color: #345;
  text-decoration: none;
}
.container-picture {
  margin-top: 50px;
}
.picture {
  width: 200px;
  height: 200px;
  border-radius: 50% !important;
}
.container-title {
  display: flex;
  align-items: center;
  justify-content: center;
}
.title {
  color: #2ecc71 !important;
  margin-top: 15px;
  font-weight: 700;
}
.content-bio {
  margin-top: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.social-content {
  margin-top: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
.icons-social {
  margin: 10px 10px;
}
.social-media {
  margin-left: 10px;
  margin-top: 10px;
}
.content-social-media {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  margin-bottom: 10px;
}
.title-git{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin-top: 16px;
}
.box{
  
  border: 1px solid #e1e4e8;
  border-radius: 6px;
}
.box p {
  background: #FFF !important;
  color: #0366d6 !important;
}
@media (max-width: 500px) {
  /* .social-content{
  } */
}
</style>
