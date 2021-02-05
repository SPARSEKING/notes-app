<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <h1 class="container-title">{{ title }}</h1>
        <message v-if="message" :message='message'/>
        <new-note :note='note' @addNote='addNote'/>
       <notes :notes='notes' @remove='removeNote'/>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
// eslint-disable-next-line import/extensions
import message from '@/components/Message';
// eslint-disable-next-line import/extensions
import newNote from '@/components/NewNote';
import notes from '@/components/Notes';

export default {
  components: {
    message,
    newNote,
    notes,
  },
  data() {
    return {
      title: 'Notes App',
      message: null,
      note: {
        title: '',
        description: '',
      },
      notes: [
        {
          title: 'Vue',
          description: 'Vue is very nice framework!',
          date: new Date(Date.now()).toLocaleString(),
        },
        {
          title: 'Angular',
          description: 'Angular is a not bad framework',
          date: new Date(Date.now()).toLocaleString(),
        },
      ],
    };
  },
  methods: {
    // eslint-disable-next-line consistent-return
    addNote() {
      const { title, description } = this.note;
      if (title === '') {
        this.message = 'Title can`t be blank!';
        return false;
      }
      this.notes.push({
        title,
        description,
        date: new Date(Date.now()).toLocaleString(),
      });
      this.message = null;
      this.note.title = '';
      this.note.description = '';
    },
    removeNote(index) {
      this.notes.splice(index, 1);
    }
  },
};
</script>

<style>
</style>
