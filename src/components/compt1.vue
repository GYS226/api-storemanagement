<template>
  <div class="search">
    <h1>Github API fetching</h1>
    <!-- v-model: trandsfer l'info vers la variable -->
    <input type="text" v-model="username" placeholder="Search">

    <!-- @click est un raccourcis de v-on:click -->
    <button @click="getRepos">get repo</button>
    <p>{{error}}</p>
    <!-- v-if: ne afficher que si if est true -->
    <h4 v-if="quantity > 0">Number : {{quantity}} repositories found</h4>

    <!-- affichage du resultat -->
    <ul id="repo">
      <li v-for="repo in repos" :key="repo.id">
        <span>{{repo.name}}</span> <span>{{repo.created_at}}</span> <span>{{repo.size}}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'compt1',
  data(){
    return{
      username:null,
      repos:null,
      quantity: null,
      error:null,
    }
  },
  methods:{
    getRepos:function(){
      return this.axios
      .get(`https:/api.github.com/users/${this.username}/repos`)
      .then(response => {
        this.repos = response.data;
        this.quantity = response.data.length;
      })
      .catch(error => {
        this.error = error;
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
h1{
  text-align: center;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-weight: 300px;
  font-style: italic;
}

button{
  background-color: grey;
  color: white;
  height: 35px;
  font-style: italic;
  text-align: center;
}

input{
  width: 250px;
  height: 30px;
}

button, input{
  margin-left: 10px;
}

#repo{
  text-align: start;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  font-style: italic;
  background-color: grey;
  color: white;
}
</style>
