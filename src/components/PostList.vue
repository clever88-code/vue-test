<template>
    <div>
        <h4>Список пользоватей</h4>
        <post-item v-for="post in posts" :post="post" />
    </div>

</template>

<script>
import PostItem from './PostItem.vue';
export default {
    components: {PostItem},
    props: {
        posts: {
            type: Array,
            required: true 
        }
    }

}

</script>

<style scoped>

</style>