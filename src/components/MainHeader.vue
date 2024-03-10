<template>
    <MainNavbar />
</template>


<script>
import MainNavbar from '@/components/MainNavbar.vue';

export default {
    setup() {
        const testText = 'Jimmy Proba';
        return {
            testText
        }
    },
    components: {
        MainNavbar
    }
}
</script>


//CSS
<style scoped>

</style>