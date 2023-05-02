<template>
  <p :class="['note-item', noteProps.completed ? 'is-completed' : '']">
    <input
      type="checkbox"
      :checked="noteProps.completed"
      @change="markItemCompleted"
    />
    {{ noteProps.title }}
    <button class="del-btn" @click="deleteItem">Xóa</button>
  </p>
</template>

<script>

export default {
  name: 'NoteItem',
  props: ['noteProps'],
  setup(props, context) {
    const markItemCompleted = () => {
      context.emit('item-completed', props.noteProps.id)
    }

    const deleteItem = () => {
      context.emit('delete-item', props.noteProps.id)
    }

    return {
      markItemCompleted,
      deleteItem
    }
  }
}
</script>

<style>
.note-item {
  background: #f4f4f4;
  padding: 10px;
  margin: 0;
  border-bottom: 1px #ccc dotted;
}

.is-completed {
  text-decoration: line-through;
}

.del-btn {
  background: #fc0707;
  color: #fff;
  border: none;
  cursor: pointer;
  float: right;
}
</style>