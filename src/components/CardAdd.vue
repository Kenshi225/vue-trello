<template>
  <form class="addcard" @subimit.prevent="addCardToList">
    <input v-model="body" 
      type="text"
      class="text-input"
      placeholder="Add new card"
      @focusin="editing"
      @focusout="edited">
      <button type="submit" class="add-button">Add</button>
  </form>
</template>

<script>
export default {
  props: {
    listIndex: {
      type: Number,
      required: true,
    }
  },
  data: function() {
    return {
      body: '',
      isEditing: false,
    }
  },
  methods: {
    editing: function() {
      this.isEditing = true
    },
    edited: function() {
      this.isEditing = false
    },
    addCardToList: function() {
      this.$store.dispatch('addCardToList', { body: this.body, listIndex: this.listIndex })
      this.bddy = ''
    }
  }
}
</script>
