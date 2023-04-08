<template>
  <div class="hello">
    <div class="button-set">
      <button @click="setEditorOptions">togleToolbar</button>
      <button @click="togleLockContent">lockContent</button>
    </div>
    <quill-editor v-model = "content" :options = "editorOptions" :disabled='lockContent'></quill-editor>
  </div>
</template>

<script>

import { quillEditor } from "vue-quill-editor";
import "quill/dist/quill.core.css";
import "quill/dist/quill.snow.css";

export default {

  name: 'HelloWorld',
  components:{
    quillEditor
  },
  created(){
    this.setEditorOptions();
  },
  data () {
    return {
      content:'handler',
      lockContent:false,
      toggleToolbar:false,
      editorOptions:{
        placeholder:'',
        modules:{
          toolbar: {
            container:[],
            handlers:{}
          }
        }
      }
    }
  },
  methods:{
    setEditorOptions(){
      if(this.toggleToolbar){
        this.editorOptions.modules.toolbar.container = false;
        console.log('hide toolbar');
      }else{
        this.editorOptions.modules.toolbar.container = 
        [
          ["bold", "italic", "underline", "strike"],
          [
            { color: 
            [
              '#000000', '#e60000', '#ff9900', '#ffff00', '#008a00', '#0066cc', '#9933ff',
              '#ffffff', '#facccc', '#ffebcc', '#ffffcc', '#cce8cc', '#cce0f5', '#ebd6ff',
              '#bbbbbb', '#f06666', '#ffc266', '#ffff66', '#66b966', '#66a3e0', '#c285ff',
              '#888888', '#a10000', '#b26b00', '#b2b200', '#006100', '#0047b2', '#6b24b2',
              '#444444', '#5c0000', '#663d00', '#666600', '#003700', '#002966', '#3d1466',
            ] },
           { background: [] },
          ],
        ];
        this.editorOptions.modules.toolbar.handlers = {
        }
      }
      this.toggleToolbar = !this.toggleToolbar;
    },
    togleLockContent(){
      this.lockContent = !this.lockContent;
    },

  }
}
</script>


<style scoped>
.button-set{
  text-align: center;
}

</style>
