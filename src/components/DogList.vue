<template>
    <div class="my-10">
        <div class="flex flex-col items-center justify-center">
             <h1 class="text-center mb-4 text-5xl font-semibold">Dog Images</h1>
            <input type="text" name="search" id="search" placeholder="Search for a dog / breed" class="py-2 border-gray-500 rounded-[8px] placeholder:text-black focus:outline-orange-900 border-[1px] px-4 w-[50vw]"/>
        </div>
        <img src=".../assets/loadingDog.jpg" alt="doj">
        <div class="mt-10 grid grid-cols-3 gap-y-2 gap-x-4 mx-20">
            <div class="" v-for="(image,index) in dogImages" :key="index">
                <router-link to="/dog/1">
                    <img v-lazy="{ src: image, loading: '@/assets/loadingDog.jpg', error: '.@/assets/loadingDog.jpg' }" :src="image" class="h-[300px] w-[380px]" alt="Dog">
                </router-link>
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
            dogImages:[],
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
  
   