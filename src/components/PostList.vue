<template>
    <div v-if="posts.length > 0">
        <h4>Список постов</h4>
        <post-item v-for="post in posts" :key ="post.id" @remove="$emit('remove', post)" :post="post" />
    </div>
    <h2 v-else style="color: red;" >
        Список постов пуст
    </h2>

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