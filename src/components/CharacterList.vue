<template>
    <div class="container">
        <h2>Characters List</h2>
        <div class="row gy-4" v-if="!store.loading">
            <div class="col-12 col-md-6 col-lg-3" v-for="character in store.characters" :key="character.id">
                <CardComponent :id="character.id" :title="character.name" :image="character.image" :status="character.status" :text="character.species" :subtext="character.gender"/>
            </div>
        </div>
        
            <ApiLoader v-else />
        
        
        <!-- <ul>
            <li v-for="character in store.characters" :key="character.id">
                {{ character.name }} {{ character.status }} {{ character.species }}
            </li>
        </ul> -->
    </div>
</template>

<script>
import { store } from '../store.js';
import ApiLoader from './ApiLoader.vue';
import CardComponent from './CardComponent.vue';
    export default {
        name: 'CaracterList',
        components: {
            ApiLoader,
            CardComponent
        },
        data() {
            return {
                store,
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>