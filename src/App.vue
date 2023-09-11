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
        {id: 1, title: 'Vue', body: 'типо описание1'},
        {id: 2, title: 'Vue2', body: 'типо описание2'},
        {id: 3, title: 'Vue3', body: 'типо описание3'},
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
  margin: 0;
  padding: 0;
  box-sizing: border-box ;

}



</style>
