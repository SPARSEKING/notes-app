<template>

<div class="notes">
    <div class="note" v-for='(note, index) in notes' :key='index'>
        <div class="note-header">
            <p >{{ note.title }}</p>
            <p style="cursor: pointer;" @click="removeNote(index)">x</p>
        </div>
        <div class="note-body">
            <p class="descr">{{ note.description }}</p>
            <span class="date">{{ note.date }}</span>
        </div>
    </div>
</div>
    
</template>

<script>
export default {
    props: {
        notes: {
            type: Array,
            required: true
        }
    },
    methods: {
        removeNote(index) {
            this.$emit('remove', index);
        }
    }
}
</script>