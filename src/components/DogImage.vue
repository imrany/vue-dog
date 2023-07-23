<script>
import { AdvancedImage } from '@cloudinary/vue';
import { Cloudinary } from '@cloudinary/url-gen';
import {Transformation} from '@cloudinary/url-gen';

// Import required actions.
import {thumbnail, scale} from "@cloudinary/url-gen/actions/resize";
import {sepia} from "@cloudinary/url-gen/actions/effect";
import {source} from "@cloudinary/url-gen/actions/overlay";
import {opacity,brightness} from "@cloudinary/url-gen/actions/adjust";

import FilterButtons from "./FilterButtons.vue"

// Create a Cloudinary instance and set your cloud name.
const cld = new Cloudinary({
    cloud: {
        cloudName: 'demo',
    }
})
// Instantiate a CloudinaryImage object for the image with the public ID, 'front_face'.
const myImg = cld.image('front_face');
// Apply the transformation.
myImg.effect(sepia()).format('png')

export default {
    props: ['image'],
    components:{
        // FilterButtons
        AdvancedImage
    },
    data() {
        return {
            myImg,
        }
    }
}
</script>

<template>
    <div class="flex flex-col h-[100vh] justify-center items-center">
        <div class="flex">
            <img :src="image" alt="Dog Image" class="max-w-[500px] max-h-[500px]">
            <AdvancedImage :cldImg="myImg"/>
            <!-- <FilterButtons/> -->
            <div class="ml-6 flex flex-col">
                <p class="text-xl mb-4">Apply filters</p>
                <button class="w-[100px] h-[40px] flex justify-center items-center rounded-[10px] bg-black text-white">Cartoonify</button>
                <button class="w-[100px] my-4 h-[40px] flex justify-center items-center rounded-[10px] bg-black text-white">Grayscale</button>
                <button class="w-[100px] h-[40px] flex justify-center items-center rounded-[10px] bg-black text-white">Sepia</button>
            </div>
        </div>
        <!-- Add your code to display more details about the dog image here -->
    </div>
</template>
  