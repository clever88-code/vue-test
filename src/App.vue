<template>
  <div class = "app">
    <div class="menu">


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
    />
    </div>

  </div>
</template>

<script>
import PostForm from './components/PostForm.vue';
import PostList from './components/PostList.vue';
import MyButton from './components/UI/MyButton.vue';
import MyDialog from './components/UI/MyDialog.vue';


export default {
  components: {
    PostList, PostForm,
    MyDialog,
    MyButton
},
  data() {
    return { 
      posts: [
        {id: 1, title: 'Vue', body: 'типо описание1'},
        {id: 2, title: 'Vue2', body: 'типо описание2'},
        {id: 3, title: 'Vue3', body: 'типо описание3'},
      ],
      dialogVisible: false,

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
    }

    
  }
}

</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box ;

}
.menu {
  
  width: 50%;
  display: block;
  margin: 0% auto;
}

.mb-10 {
  margin-bottom: 10px;
}


</style>
