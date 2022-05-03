<script setup>
import TextEditor from "../components/TextEditor.vue";
</script>
<template>
  <div class="grid-wrapper">
    <div class="editor editor-1">
      <TextEditor
        textareaid="editor-1"
        :errorLines="[1]"
        :currentStepLine="0"
      />
    </div>
    <div class="editor editor-2">editor-2</div>
    <div class="maingrid"></div>
    <div class="editor editor-3">editor-3</div>
    <div class="editor editor-4">editor-4</div>
  </div>
</template>
<style scoped>
.grid-wrapper {
  display: grid;
  grid-template-columns: 25% 50% 25%;
  grid-template-rows: 1fr 25vw 25vw 1fr;
  grid-template-areas:
    "ed1 . ed2"
    "ed1 maingrid ed2"
    "ed3 maingrid ed4"
    "ed3 . ed4";
  gap: 5px;
}

div.editor > textarea {
  width: 95%;
  height: 95%;
}
div.editor {
  text-align: center;
}

.editor-1 {
  background: tomato;
  grid-area: ed1;
}
.editor-2 {
  background: red;
  grid-area: ed2;
}
.editor-3 {
  grid-area: ed3;
  background: green;
}
.editor-4 {
  grid-area: ed4;
  background: yellow;
}
.maingrid {
  background: lightcoral;
  grid-area: maingrid;
}
</style>
