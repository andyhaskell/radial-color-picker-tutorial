<template>
  <form>
    <div>
      <h3> Select a color</h3>
      <!--
        Now in addition to controlling the component's hue value with the
        radial color picker, we're v-binding its hue, saturation, and
        luminosity data values to the radial-color-picker component, allowing
        their values to display in the center dot of the color picker.
      -->
      <radial-color-picker
        aria-label="hue radial slider"
        v-model="hue"
        :hue=hue
        :saturation=saturation
        :luminosity=luminosity
        @input="selectColor"
      />
    </div>
    <div>
      <h3>Select color saturation</h3>
      <!--
        aria-valuetext lets the selected saturation read in screen readers as
        "100 percent saturation", rather than just "100".
      -->
      <input
        aria-label="saturation horizontal slider"
        aria-valuetext="percent saturation"
        type="range"
        v-model="saturation"
        @input="selectColor"
      />
    </div>
    <div>
      <h3>Select color luminosity</h3>
      <input
        aria-label="luminosity horizontal slider"
        aria-valuetext="percent luminosity"
        type="range"
        v-model="luminosity"
        @input="selectColor"
      />
    </div>
  </form>
</template>

<script>
import ColorPicker from '@radial-color-picker/vue-color-picker';

export default {
  name: 'ColorPicker',
  components: {
    'radial-color-picker': ColorPicker
  },

  // have the three parts of the color in the data of the app.
  data: function() {
    return {
      hue: 0,
      saturation: 100,
      luminosity: 50,
    }
  },

  // now we are deriving all three parts of an HSL color from the component's
  // data.
  methods: {
    selectColor() {
      this.$emit(
        'color-change',
        `hsl(${this.hue}, ${this.saturation}%, ${this.luminosity}%)`,
      );
    },
  },
}
</script>

<style>
@import '~@radial-color-picker/vue-color-picker/dist/vue-color-picker.min.css';
</style>