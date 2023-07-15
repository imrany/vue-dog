<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <h1 class="text-center mb-4">Dog Images</h1>
            </div>
            <div class="col-12">
                <div class="card-columns">
                    <div class="card col-lg-3 col-md-4 col-sm-6" v-for="(image,index) in dogImages" :key="index">
                        <img v-lazy="image" :src="image" class="image" alt="Dog">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
  
<script>
import { mapGetters } from 'vuex';
import DogService from '../services/DogService';

export default {
    data(){
        return {
            dogImages:[]
        };
    },
    computed: {
        ...mapGetters(['getDogImages']),
    },
    mounted() {
        this.fetchDogImages();
    },
    methods: {
        async fetchDogImages() {
            try {
                // const breeds = await DogService.getBreeds();
                // const randomBreed = Object.keys(breeds)[0]; // Fetch images for the first breed in the list
                // const randomImage = await DogService.getRandomImageByBreed(randomBreed);
                // const images = await DogService.getImagesByBreed(randomBreed);
                // this.$store.commit('setDogImages', [...images, randomImage]);
                const images=await DogService.getDogImages();
                this.dogImages=images.data.message
                console.log(images.data)
            } catch (error) {
                console.error('Error fetching dog images:', error);
            }
        },
    },
};
</script>
  
   