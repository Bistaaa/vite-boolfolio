<template>
    <div class="row justify-content-between">
        <project-card class="my-2" v-for="project in projects" :key="project.id" :project="project" />
    </div>
</template>

<script>
import ProjectCard from '../components/ProjectCard.vue'
import axios from 'axios';

const API = "http://localhost:8000/api/v1"

export default {
    name: 'AppHome',
    components: {
        ProjectCard
    },
    data() {
        return {
            projects: []
        }
    },
    mounted() {
        axios.get(API + '/projects')
            .then(res => {

                this.projects = res.data.projects;
            })
            .catch(err => console.error(err))
    }
}
</script>