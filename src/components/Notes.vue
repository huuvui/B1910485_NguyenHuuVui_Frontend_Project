<template>
  <AddNote @add-note="addNote" />
  <NoteItem
    v-for="note in notes"
    :key="note.id"
    :noteProps="note"
    @item-completed="markComplete"
    @delete-item="deleteNote"
  />
</template>

<script>
import { ref } from 'vue'

import axios from 'axios'

import NoteItem from './NoteItem'
import AddNote from './AddNote'

export default {
  name: 'Notes',
  components: { NoteItem, AddNote },
  setup() {
    const notes = ref([])

    const getAllNotes = async () => {
      try {
        const res = await axios.get(
          'http://localhost:8000/api/notes/'
        )
        notes.value = res.data
      } catch (error) {
        console.log(error)
      }
    }

    getAllNotes()

    const markComplete = id => {
      notes.value = notes.value.map(note => {
        if (note.id === id) note.completed = !note.completed
        return note
      })
    }

    const deleteNote = async id => {
      try {
        await axios.delete('http://localhost:8000/api/notes/')
        notes.value = notes.value.filter(note => note.id !== id)
      } catch (error) {
        console.log(error)
      }
    }


    const addNote = async newNote => {
      try {
        const res = await axios.post(
          'http://localhost:8000/api/notes/',
          newNote
        )
        notes.value.push(res.data)
      } catch (error) {
        console.log(error)
      }
    }

    return {
      notes,
      markComplete,
      deleteNote,
      addNote
    }
  }
}
</script>

<style></style>
