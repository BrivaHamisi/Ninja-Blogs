<template>
    <div v-if="job">
        <h1>{{job.title}}</h1>
        <p>The Job Id is {{ id }}</p>
        <p>{{ job.details }}</p>
    </div>
    <div v-else>
        <p>Loading Job Details...</p>
    </div>
</template>

<script>
export default {
    props:['id'],
    data(){
        return {
            job:null
        }
    },
    mounted() {
        fetch('http://localhost:3000/jobs/'+this.id)
        .then(response => response.json())
        .then(data => this.job = data)
        .catch(err => console.log('Error:', err.message) );
    }
}
</script>

<style>

</style>