<template>
    <div>
        <h3>hello this is character.vue</h3>
        <p>{{ this.$route.params.id }}</p>

        <ul>
            <li v-for="char in character" :key="char.id">
                {{ char.name }}
                {{ char.description }}
            </li>
        </ul>
        <img :src="url" :alt="char.name">
    </div>
</template>

<script>
import { public_key } from '../marvel'
import axios from 'axios'
import { mapState } from 'vuex'
export default {
    name: 'Character',
    data(){
        return{
            url: '',
            size: 'standard_large.jpg'
        }
    },
    mounted() {
        this.$store.dispatch('getCharacter', this.$route.params.id)
        this.getImage()
    },
    methods: { 
        getImage(){
            this.url = `${this.preUrl}${this.size}`
        }
    },
    computed: {
        ...mapState({
            character: state => state.character,
            preUrl: state => state.url
        })
    }
}
</script>

<style scoped>

</style>