<template>
  <h1>Jobs</h1>
  <div v-if="jobs.length">
    <div v-for="job in jobs" :key="job.id" class="job">
      <router-link :to="{name: 'jobdetails', params: {id:job.id}}"><h2>{{ job.title }}</h2></router-link>
    </div>
  </div>
  <div v-else>
    <p>Loading Jobs...</p>
  </div>
</template>

<script>
export default {
data(){
    return {
      jobs:[

      ],
      // jobs:[
      //   {title: 'Software Engineer', id:1, details: 'Software Engineer at ABC Corp'},
      //   {title: 'Senior Software Engineer', id:2, details: 'Senior Software Engineer at XYZ Corp'  },
      //   {title: 'Junior Software Engineer', id:3, details: 'Junior Software Engineer at ABC Corp'  },
      //   {title: 'Frontend Developer', id:4, details: 'Frontend Developer at XYZ Corp'   },
      //   {title: 'Backend Developer', id:5, details: 'Backend Developer at ABC Corp'   },
      // ],
    }
  },
  mounted() {
    fetch('http://localhost:3000/jobs')
    .then(response => response.json())
    .then(data => this.jobs = data)
    .catch(err => console.log('Error:', err.message) );
  }
}
</script>

<style>
.job h2 {
  background: #f4f4f4;
  padding: 20px;
  border-radius: 10px;
  margin: 10px auto;
  max-width: 600px;
  cursor: pointer;
  color: #444;
}
.job h2:hover {
  background: #ddd;
}
.job a {
  text-decoration: none;
}
button {
  margin: 0 10px;
  padding: 10px;
  border: none;
  border-radius: 4px;
}
</style>