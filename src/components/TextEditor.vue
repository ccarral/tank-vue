<template>
  <div class="editor-container">
    <textarea
      v-if="editable"
      v-model="code"
      class="editor editor-size"
      @focusout="editable = false"
    ></textarea>
    <table v-if="!editable" @click="editable = true" class="editor editor-size">
      <tr v-for="(line, idx) in lines" :key="idx" class="editor-line"
      :class="{'error-line':errorArray[idx]}">
        {{
          line
        }}
      </tr>
    </table>
  </div>
</template>
<script>
export default {
  props: { errorLines: Array },
  data() {
    return {
      code: "avanza;\ngira derecha\nvar x = radar;",
      editable: false,
    };
  },
  computed: {
    lines() {
      return this.code.split("\n");
    },
    errorArray() {
      const errorArray = new Array(this.lines.length);
      for (let i = 0; i < this.lines.length; i++) {
        if (this.errorLines.includes(i)) {
          errorArray[i] = true;
        } else {
          errorArray[i] = false;
        }
      }
      return errorArray;
    },
  },
};
</script>
<style scoped>
.editor {
  font-family: monospace;
  background-color: #fafafa;
}
.editor-size {
  resize: none;
}
.editor-table{
}
.editor-container{
  text-align:left;
  width: 80%;
  height: 100%;
}
.error-line{
    background-color: #ff5959;
}
</style>
