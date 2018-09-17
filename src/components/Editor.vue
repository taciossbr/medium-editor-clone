<template>
  <div class="editor-wrap">
    <div 
      class="editor" 
      contenteditable="true" 
      v-on:input="change"
      ref="editor"
      ></div>
      <p v-on:click="newParagraph" class='new-paragraph'>Escreva Aqui</p>
  </div>
</template>

<script>
export default {
  name: 'Editor',
  props: ['content'],
  mounted() {
    document.execCommand("defaultParagraphSeparator", false, "p");
    document.execCommand("insertBrOnReturn", false, false);
    this.$refs.editor.innerHTML = this.content || '<h1></h1>';
  },
  methods: {
    change() {
      if(!this.$refs.editor.innerHTML) {
        this.$refs.editor.innerHTML = '<h1></h1>'
        // this.isEmpty = true;
      } else {
        // this.isEmpty = false;
        this.$emit('update', this.$refs.editor.innerHTML);
      }
    },
    newParagraph() {
      // this.$refs.editor.focus();
      // console.log(this.$refs.editor);
      let char = this.$refs.editor.childNodes.length;
      // console.log(char)
      let sel = window.getSelection();
      sel.collapse(this.$refs.editor, char);
      document.execCommand("insertParagraph", false);

      
    }
  }
}
</script>

<style>
  .editor > h1:empty::after, .new-paragraph { 
    color: #cecece;
    font-style: italic;
    margin-left: 10px;
  } 
  .editor > h1:empty::after {
    content: 'Titulo';
  }
  .new-paragraph {
    content: 'Escreva Aqui';
  }
  .editor:focus {
    border: none;
    outline: none;
  }
</style>
