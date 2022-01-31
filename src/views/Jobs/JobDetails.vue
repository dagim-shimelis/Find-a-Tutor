 <template>
   <h1>{{job.title}}</h1>
   <h2>{{job.id}}</h2>
   <h3>{{job.details}}</h3>
 </template>
 
 <script>
 export default {
 props:['id'],
 data(){
     return{
         job: {}
     }
 },

mounted(){
    fetch('http://localhost:3000/jobs/' + this.id)
    .then(res => res.json())
    .then(data => this.job = data)
    .catch(err => console.error(err.message))
}
 }
 </script>
 
 <style>
 
 </style>