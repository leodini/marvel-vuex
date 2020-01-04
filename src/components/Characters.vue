<template>
    <div>
        <h3>hello this is characters.vue</h3>
        <ul>
            <li v-for="(character, index) in characters" :key="index">
                <router-link 
                :to="{ name: 'character', params: { id: character.id}}">
                {{ character.name }}
                </router-link>
            </li>
        </ul>
    </div>    
</template>

<script>
import { mapState } from 'vuex'
import { public_key, secret_key } from '../marvel.js'
import axios from 'axios'
export default {
    name: 'Characters',
    
    mounted(){
        this.$store.dispatch('getCharacters')
    },
    methods: {
    
      
    },
    computed: {
        ...mapState({
            characters: state => state.characters
        })
    }
}

</script>

<style scoped>

</style>