<template>
  <div id="app">
    <ckeditor :editor="editor" v-model="editorData" :config="editorConfig" @ready="onReady"></ckeditor>
  </div>
</template>

<script>
import DecoupledEditor from '@ckeditor/ckeditor5-build-decoupled-document';
import "@kimnagui/ckeditor5-translation-ko";
// import ClassicEditor from '@ckeditor/ckeditor5-editor-classic/src/classiceditor';
// import EssentialsPlugin from '@ckeditor/ckeditor5-essentials/src/essentials';
// import BoldPlugin from '@ckeditor/ckeditor5-basic-styles/src/bold';
// import ItalicPlugin from '@ckeditor/ckeditor5-basic-styles/src/italic';
// import LinkPlugin from '@ckeditor/ckeditor5-link/src/link';
// import ParagraphPlugin from '@ckeditor/ckeditor5-paragraph/src/paragraph';

export default {
  name: 'App',
  components: {
  },
  data: function() {
    return {
      editor: DecoupledEditor,
      editorData: '<p> Content of the editor.</p>',
      editorConfig: {
        toolbar: {
          items: [
            'heading', '|',
            'alignment', '|',
            'bold', 'italic', 'strikethrough', 'underline', 'subscript', 'superscript', '|',
            'link', '|',
            'bulletedList', 'numberedList', 'todoList',
            '-', // break point
            'fontfamily', 'fontsize', 'fontColor', 'fontBackgroundColor', '|',
            'code', 'codeBlock', '|',
            'insertTable', '|',
            'outdent', 'indent', '|',
            'uploadImage', 'blockQuote', '|',
            'undo', 'redo'
          ]
        },
        language: "ko",
        indentBlock: {
            offset: 10,
            unit: 'em'
        }
      }
    }
  },
  mounted: function() {
  },
  methods: {
    onReady: function(editor) {
      console.log(editor);
      editor.ui.getEditableElement().parentElement.insertBefore(
                    editor.ui.view.toolbar.element,
                    editor.ui.getEditableElement()
                );
    }
  }
}
</script>

<style>
 .vdr {
    border: 1px dashed black;
  }
</style>
