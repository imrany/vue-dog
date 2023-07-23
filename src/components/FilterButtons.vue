<template>
    <div class="ml-6 flex flex-col">
        <p class="text-xl mb-4">Apply filters</p>
        <button class="w-[100px] h-[40px] flex justify-center items-center rounded-[10px] bg-black text-white">Cartoonify</button>
        <button class="w-[100px] my-4 h-[40px] flex justify-center items-center rounded-[10px] bg-black text-white">Grayscale</button>
        <button class="w-[100px] h-[40px] flex justify-center items-center rounded-[10px] bg-black text-white">Sepia</button>
    </div>
</template>

<script>
export default {
    methods: {
        applyFilter(filterType) {
            // Emit an event with the selected filter type
            this.$emit('apply-filter', filterType);
        },
    },
};
</script>