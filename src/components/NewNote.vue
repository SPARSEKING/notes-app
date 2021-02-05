<template>
    <div class="new-note">
        <input type="text" v-model="note.title">
        <textarea v-model='note.description'></textarea>
        <button @click='addNote' class="button-new-note">NEW NOTE</button>
        </div>
</template>

<script>
export default {
  props: {
    note: {
      type: Object,
      required: true,
    },
  },
  methods: {
   addNote() {
     this.$emit('addNote', this.note);
   }
  }
};
</script>
