<script setup>
import { ref, watch } from 'vue';
import { RouterLink, RouterView, useRoute } from 'vue-router';


const frameworks = ref([
{ id: 1, name: 'Vue.js', desc: 'Progressive Framework per construir interfícies web.' },
{ id: 2, name: 'React', desc: 'Biblioteca per crear interfícies d’usuari interactives.' },
{ id: 3, name: 'Angular', desc: 'Framework complet per aplicacions empresarials.' }
])

const framework = ref(null);

const route = useRoute();
const frameworkId = parseInt(route.params.id);
/*const framework = frameworks.value.find(f => f.id == frameworkId);*/
/*Funció per carregar el framework*/
const carregarFramework = (id)=> {framework.value = frameworks.value.find(f => f.id == id);}
carregarFramework(route.params.id)
watch(
    ()=>route.params.id,
    (newID)=>{
        carregarFramework(newID)
    }
)

</script>

<template>
    <h1>{{framework.name}}</h1>
    <p>{{framework.desc }}</p>

    
</template>