<template>
  <div class = "app">

    <form @submit.prevent>
      <h1>Cоздание поста</h1>
      <input v-bind:value="title" @input="title = $event.target.value" class="input" type="text" placeholder="Название">
      <input v-bind:value="body" @input="body = $event.target.value" type="text" placeholder="Описание">
      <button class="btn" @click="createPost">Cоздать</button>
 
    </form>

    <div class="post" v-for="post in posts">
      <div><strong>Название</strong> {{ post.title }}</div>
      <div><strong>Описание</strong> {{ post.body }}</div>

    </div>



  </div>
</template>

<script>

export default {
  data() {
    return { 
      posts: [
        {id: 1, title: 'Vue', body: 'типо описание'},
        {id: 2, title: 'Vue2', body: 'типо описание'},
        {id: 3, title: 'Vue3', body: 'типо описание'},
      ],
      title: '',
      body: '',
    }
  },
  methods: {
    createPost() {
      const newPost = {
        id: Date.now(),
        title: this.title,
        body: this.body,
      }
      this.posts.push(newPost);
      this.title = '';
      this.body = '';

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

form {
  display: flex;
  flex-direction: column;
}

.btn {
  margin-top: 15px;
  align-self: flex-start;
  padding: 10px 15px;
  background: none;
  color: orange;
  border: 1px solid orange;
}

.app{
  padding: 20px;
}
.post {
  padding: 15px;
  border: 3px solid orange ;
  margin-top: 15px;

}

.input {
  width: 100%;
  border: 1px solid orange;
  padding: 10px 15 px;
  margin-top: 15px;

}

</style>
