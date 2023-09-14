<template>
  <div class = "app">
    <div class="conteiner1">


    <h1 class="mb-10" >Странице с постами</h1>
    <my-button @click="showDialog" class="mb-10" >Создать пост</my-button>
    <my-dialog v-model:show="dialogVisible">
      <post-form
      @create="createPost"
      />
    </my-dialog>
    <post-list 
    :posts="posts"
    @remove="removePost"
    v-if="!isPostLoading"
    />
    <div v-else >
      Идёт загрузка
    </div>
    </div>

  </div>
</template>

<script>
import PostForm from './components/PostForm.vue';
import PostList from './components/PostList.vue';
import MyButton from './components/UI/MyButton.vue';
import MyDialog from './components/UI/MyDialog.vue';
import axios from 'axios';

export default {
  components: {
    PostList, PostForm,
    MyDialog,
    MyButton
},
  data() {
    return { 
      posts: [],
      dialogVisible: false,
      isPostLoading: false,

    }
  },
  methods: {
    createPost(post) {
      console.log(post)
      this.posts.push(post);
      this.dialogVisible = false;



    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try{
        this.isPostLoading = true;
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
        console.log(response)
        this.posts = response.data;

      } catch (e) {
        alert("ошибка")
      } finally {
        this.isPostLoading = false;
      }

    },

    
  },
  mounted() {
    this.fetchPosts();
  }
}

</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box ;

}
.conteiner1 {
  
  width: 50%;
  display: block;
  margin: 0% auto;
}

.mb-10 {
  margin-bottom: 10px;
}


</style>
