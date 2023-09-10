<template>
    <form @submit.prevent>
      <h1>Cоздание поста</h1>
      <input v-model="post.title" class="input" type="text" placeholder="Название">
      <input v-model="post.body" type="text" placeholder="Описание">
      <button class="btn" @click="createPost">Cоздать</button>
 
    </form>
</template>

<script>
export default {
    data() {
        return {
            post: {
                title: '',
                body: '',
            }
        }
    },
    methods: {
        createPost() {
            this.post.id = Date.now();
            this.$emit('create', this.post, 'second', '3param')
            // удаляем данные
            this.post = {
                title: '',
                body: '',
            }
        }


    },
}

</script>

<style>

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


.input {
  width: 100%;
  border: 1px solid orange;
  padding: 10px 15 px;
  margin-top: 15px;

}

</style>