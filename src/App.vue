<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col">
          <div class="container-title">
            <h1 class="title">Em manutenção</h1>
          </div>
        </div>
      </div>
    </div>
    
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import axios from "axios";
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
    this.getProfile();
    this.getReposOne();
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
      const repo = axios.get(
        "https://api.github.com/repos/renatoReboucas/api-lumen"
      );
      this.repos = repo.data;
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
  font-weight: 600;
  font-size: 30px;
}
.content-bio {
  margin-top: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  font-size: 12px;
}
.social-content {
  margin-top: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  font-size: 10px;
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
.title-git {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin-top: 16px;
}
.box {
  border: 1px solid #e1e4e8;
  border-radius: 6px;
}
.box p {
  background: #fff !important;
  color: #0366d6 !important;
}
.header {
    display: flex;
    flex-direction: row-reverse;
    border: 1px solid #2ecc71;
    /* width: 1440px; */
    height: 80px;
}
@media (max-width: 500px) {
  /* .social-content{
  } */
}
</style>
