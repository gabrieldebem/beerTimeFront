<template>
    <div class="flex">
        <button type="button" 
            class="inline-flex items-center px-4 py-2 border border-transparent shadow-sm text-sm font-medium rounded-md
            text-white bg-yellow-600 hover:bg-yellow-700 focus:outline-none focus:ring-2 focus:ring-yellow-500 content-center"
            @click="this.getTimeToBeer()">
            <cursor-click-icon class="-ml-1 mr-2 h-5 w-5" aria-hidden="true" />
            It's time to beer?
        </button>
    </div>
    <div class="text-amber-500 text-center mt-4" 
        v-if="timeToBeer">
        {{timeToBeer.data.message}}
    </div>
    <div class="text-amber-500 text-center mt-4" 
        v-if="errorMessage">
        {{errorMessage}}
    </div>
</template>

<script>
import axios from 'axios';
import CursorClickIcon from './icons/CursorClickIcon.vue';

export default {
  components: { CursorClickIcon },
    methods: {
        getTimeToBeer() {
            axios.get('https://beer-time-api.herokuapp.com/')
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
