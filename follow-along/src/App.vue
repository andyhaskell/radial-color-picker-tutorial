<template>
  <div class="whole-thing">
    <h1 :style="{color: color}">{{ message }}</h1>
    <div aria-label="message input">
      <input type="text" v-model="message" />
    </div>
    <color-picker
      aria-label="color picker"
      @color-change="colorChange"
      :colors="['black', 'red', 'green', 'blue']"
    ></color-picker>
  </div>
</template>

<script>
import ColorPicker from './components/ColorPicker.vue';

export default {
  name: 'App',
  components: {
    'color-picker': ColorPicker,
  },

  data() {
    return {
      color: 'black',
      message: 'write a message',
    };
  },

  methods: {
    colorChange(color) {
      this.color = color;
    },
  },
}
</script>