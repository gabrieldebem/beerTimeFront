<template>
    <div>
        <button 
            class="bg-gray-500 rounded p-2 text-yellow-500"
            @click="this.getTimeToBeer()">
            Its time to Beer?
        </button>
    </div>
    <div class="text-amber-500 text-center mt-4" 
        v-if="timeToBeer">
        {{timeToBeer.data.message}}
    </div>
    <div v-if="errorMessage">
        {{errorMessage}}
    </div>
</template>

<script>
import axios from 'axios';

export default {
    methods: {
        getTimeToBeer() {
            axios.get('http://localhost:4000/')
            .then((response) => {
                this.timeToBeer = response;
            })
            .catch((error) => {
                console.log(error)
                this.errorMessage = 'Fail to get correctly data.'
            })
        }
    },
    data() {
        return {
            timeToBeer: '',
            errorMessage: ''
        }
    },
}
</script>

<style>

</style>
