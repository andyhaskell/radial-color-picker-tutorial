<template>
  <form>
    <h3> Select a color</h3>
    <radial-color-picker
      aria-label="hue radial selector"
      @input="selectColor"
    />
  </form>
</template>

<script>
import ColorPicker from '@radial-color-picker/vue-color-picker';

export default {
  name: 'ColorPicker',
  components: {
    'radial-color-picker': ColorPicker
  },
  methods: {
    selectColor(hue) {
      this.$emit('color-change', `hsl(${hue}, 100%, 50%)`);
    },
  },
}
</script>

<style>
@import '~@radial-color-picker/vue-color-picker/dist/vue-color-picker.min.css';
</style>