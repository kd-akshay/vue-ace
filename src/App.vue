<template>
  <div class="ace-container">
    <!-- ID is used in official documents, it is forbidden to use it here, it is easy to cause problems after packaging later, just use ref or DOM -->
    <div class="ace-editor" ref="ace">select * from</div>
  </div>
</template>

<script>
import ace from 'ace-builds';
import 'ace-builds/webpack-resolver';
import 'ace-builds/src-noconflict/theme-terminal';
import 'ace-builds/src-noconflict/mode-sql';
('');
import 'ace-builds/src-noconflict/ext-language_tools';

export default {
  mounted() {
    this.aceEditor = ace.edit(this.$refs.ace, {
      fontSize: 14,
      theme: this.themePath,
      mode: this.modePath,
      tabSize: 4,
    });

    this.aceEditor.setOptions({
      enableBasicAutocompletion: true,
      enableSnippets: true,
      enableLiveAutocompletion: true,
      indentedSoftWrap: true,
      fixedWidthGutter: true,
      animatedScroll: true,
      readOnly: false,
      highlightActiveLine: true, // boolean
      highlightSelectedWord: true,
    });
  },
  data() {
    return {
      aceEditor: null,
      themePath: 'ace/theme/terminal', //If webpack-resolver is not imported, the module path will report an error
      modePath: 'ace/mode/sql', //Same as above
    };
  },
};
</script>

<style scoped>
.ace-editor {
  /* width: 100%; */
  min-height: 98vh;
  max-height: 98vh;
}
</style>
