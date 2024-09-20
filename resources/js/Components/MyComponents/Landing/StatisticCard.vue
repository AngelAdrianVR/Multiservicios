<template>
    <main class="bg-[#5B5B5B] rounded-lg shadow-md shadow-black/50 p-4 text-center">
        <p class="text-white text-lg italic">{{ label ?? '' }}</p>
        <p class="text-[#1ABACF] font-bold text-4xl mt-4">{{ value ?? '' }}</p>
    </main> 
</template>

<script>
export default {
data() {
    return {

    }
},
props:{
    label: String,
    value: String
}
}
</script>