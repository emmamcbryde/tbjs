<template>
  <v-btn class="jbtn-file">
    {{ title }}
    <input
      multiple
      type="file"
      @change="fileSelected"
    >
  </v-btn>
</template>

<script>
export default {
  props: {
    selectedCallback: {
      type: Function,
      default: () => {}
    },
    title: {
      type: String,
      default: 'Upload'
    }
  },
  methods: {
    fileSelected (e) {
      if (this.selectedCallback) {
        if (e.target.files[0]) {
          this.selectedCallback(e.target.files)
        } else {
          this.selectedCallback(null)
        }
      }
    }
  }
}
</script>

<style scoped>
.jbtn-file {
  cursor: pointer;
  position: relative;
  overflow: hidden;
}
.jbtn-file input[type='file'] {
  position: absolute;
  top: 0;
  right: 0;
  min-width: 100%;
  min-height: 100%;
  text-align: right;
  filter: alpha(opacity=0);
  opacity: 0;
  outline: none;
  cursor: inherit;
  display: block;
}
</style>
