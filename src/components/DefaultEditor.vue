<template>
    <ckeditor :editor="ClassicEditor" v-model="editorData" :config="editorConfig"></ckeditor>
</template>

<script setup>
import { ref } from 'vue'
import ClassicEditor from '@ckeditor/ckeditor5-build-classic'
const editorData = ref('This is the default value.')
const editorConfig = {
    // empty
}

</script>

<style>
body {
    color: #000;
}
</style>