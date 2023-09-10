<template>
  <div class = "app">
    <post-form
    @create="createPost"
    />
    <post-list 
    :posts="posts"
    />

  </div>
</template>

<script>
import PostForm from './components/PostForm.vue';
import PostList from './components/PostList.vue';


export default {
  components: {
    PostList,PostForm
  },
  data() {
    return { 
      posts: [
        {id: 1, title: 'Vue', body: 'типо описание'},
        {id: 2, title: 'Vue2', body: 'типо описание'},
        {id: 3, title: 'Vue3', body: 'типо описание'},
      ],

    }
  },
  methods: {
    createPost(post) {
      console.log(post)
      this.posts.push(post);



    },

    
  }
}

</script>

<style>
* {
  margin: 10;
  padding: 10;
  box-sizing: border-box;

}



</style>
