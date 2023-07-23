<template>
    <div class="flex flex-col h-[100vh] justify-center items-center">
        <div class="flex">
            <img :src="image" alt="Dog Image" class="max-w-[500px] max-h-[500px]">
            <div class="ml-6 flex flex-col">
                <button class="w-[100px] h-[40px] flex justify-center items-center rounded-[10px] bg-black text-white">Cartoonify</button>
                <button class="w-[100px] my-4 h-[40px] flex justify-center items-center rounded-[10px] bg-black text-white">Grayscale</button>
                <button class="w-[100px] h-[40px] flex justify-center items-center rounded-[10px] bg-black text-white">Sepia</button>
            </div>
        </div>
        <!-- Add your code to display more details about the dog image here -->
    </div>
</template>
  
<script>

export default {
    props: ['image']
}
</script>