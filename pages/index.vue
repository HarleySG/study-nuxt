<template>
    <div>
        <ul>
            <li v-for="album in albums" :key="album.id">{{album.title}}</li>
        </ul>
    </div>
</template>

<script>
    import axios from 'axios';
    import env from './../config/env';
    export default {
        name: 'IndexPage',
        data() {
            return {
                albums: []
            }
        },
        created(){
            axios.get(`${env.endPoint}/albums`)
            .then(res => {
                console.log(res)
                let { data } = res;
                this.albums = data;
            })
        }
    }
</script>

<style>
    html {
        font-family: sans-serif;
    }
    body {
        margin: 0;
        min-height: 100vh;
        display: grid;
        grid-template-columns: 1fr;
    }
</style>
