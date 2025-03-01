<template>
    <button class="p-0 w-11 cursor-pointer rounded-full" type="button"><PlusCircleIcon class="h-12 w-12 text-green-500 p-0" @click="funcao"/></button>
</template>

<script>
import { PlusCircleIcon } from '@heroicons/vue/24/solid'
export default {
    props: {
        funcao: Function,
        
    },
    components: {
        PlusCircleIcon
    }
};
</script>

<style scoped>

</style>