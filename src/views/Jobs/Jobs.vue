<template>
  <div class="jobs">
      <h1>Jobs</h1>
      <div v-for="job in jobs" :key='job.id' class="job">

          <router-link :to="{ name:'JobDetail',  params:{ id: job.id }}">
              <h2>{{ job.title }}</h2>
          </router-link>
      </div>
  </div>
</template>

<script>
export default {
data(){
    return {
        jobs: [],
    }
},
mounted(){
    fetch("http://localhost:3000/jobs")
    .then(res => res.json())
    .then(data => this.jobs = data)
    .catch(err => console.error(err.message))
}

}
</script>

<style>
.job h2{
background-color:#f4f4f4;
padding:20px;
margin:10px auto;
cursor:pointer;
border-radius: 10px;
max-width: 600px;
color: #444;
}

.jobs h2:hover{
    background-color:#ddd;
    /* text-decoration: underline; */
    color: #42b983;
}
.jobs a{
    text-decoration:none;
}
</style>