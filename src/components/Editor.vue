<template>
  <div class="editor-wrap">
    <div 
      class="editor" 
      contenteditable="true" 
      v-on:input="change"
      ref="editor"></div>
  </div>
</template>

<script>
export default {
  name: 'Editor',
  props: ['content'],
  mounted() {
    document.execCommand("defaultParagraphSeparator", false, "p");
    this.$refs.editor.innerHTML = this.content;
  },
  methods: {
    change() {
      
      this.$emit('update', this.$refs.editor.innerHTML)
    },
}
</script>

<style scoped>
  .editor:empty::after {
    content: 'Escreva Aqui';
    color: #cecece;
    font-style: italic;
    margin-left: 10px;
  }
  .editor:focus {
    border: none;
    outline: none;
  }
</style>
