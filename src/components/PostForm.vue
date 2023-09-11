<template>
    <form @submit.prevent>
      <h1>Cоздание поста</h1>
      <input v-model="post.title" class="input" type="text" placeholder="Название">
      <input v-model="post.body" type="text" placeholder="Описание">
      <my-button class="btn" style="align-self: flex-end; margin-top: 15px;" @click="createPost">Cоздать</my-button>
 
    </form>
</template>

<script>
import MyButton from "@/components/UI/MyButton";
export default {
  components: {
    MyButton

  },
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