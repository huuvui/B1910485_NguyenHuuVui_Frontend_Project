<template>
  <form @submit="addItem">
    <input type="text" placeholder="STT" v-model="id" />
    <input type="text" placeholder="Nhập nội dung ghi chú......." v-model="title" />
    <input type="submit" value="Lưu" class="add-btn" />
  </form>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'AddNote',
  setup(props, context) {
    const title = ref('')
    const id = ref('')

    const addItem = event => {
      event.preventDefault()

      const newItem = {
        id: id.value,
        title: title.value,
        completed: false
      }

      context.emit('add-note', newItem)
      id.value = ''
      title.value = ''
    }

    return {
      id,
      title,
      addItem
    }
  }
}
</script>

<style scoped>
form {
  display: flex;
}

input[type='text'] {
  flex: 10;
  padding: 5px;
}

input[type='submit'] {
  flex: 2;
}
</style>