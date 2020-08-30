<template>
  <form>
    <h3> Select a color</h3>
    <button
      v-for="color in colors"
      :key="color"
      @click.prevent="selectColor(color)"
    >
      {{ color }}
    </button>
  </form>
</template>

<script>
export default {
  name: 'ColorPicker',
  props: ['colors'],
  methods: {
    selectColor(color) {
      this.$emit('color-change', color);
    },
  },
}
</script>