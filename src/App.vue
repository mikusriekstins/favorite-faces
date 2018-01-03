<template>
  <div id="app">

    <div class="context">
      <div class="grid grid--no-gutter">
        <aside class="col--1-4">

          <header class="header">
            <h1>Modular Scale</h1>
          </header>

          <div class="column column--with-header">
            <form class="column__inner">

              <div class="input-group">
                <label class="input__label">Font family</label>
                <select class="input input--select" v-model="fontFamily">
                  <option v-for="font in fontFamilies" v-bind:value="font.id">{{ font.name }}</option>
                </select>
              </div>

              <div class="input-group">
                <label class="input__label">Line height</label>
                <input class="input" type="number" v-model="leading" min="1" max="2" step="0.05">
              </div>

              <div class="input-group">
                <label class="input__label">Ratio</label>
                <select class="input input--select" v-model="activeRatio">
                  <option v-for="ratio in ratios" v-bind:value="ratio.val">{{ ratio.val }} - {{ ratio.name }}</option>
                </select>
              </div>

              <div class="input-group">
                <label class="input__label">Scale root</label>
                <div class="input-group__inline">
                  <input class="input input--large" type="number" v-model="scaleRoot">
                  <a class="input__minus" v-on:click="decreaseRoot"></a>
                  <a class="input__plus" v-on:click="increaseRoot"></a>
                </div>
              </div>

            </form>
          </div>

        </aside>
        <div class="col--1-12">

          <div class="column">
            <div class="column__inner column__inner--full">

              <scale v-bind:base="scaleRoot" v-bind:ratio="activeRatio"></scale>

            </div>
          </div>

        </div>
        <div class="col--2-3">

          <div class="column">
            <div class="column__inner">

              <preview v-bind:family="fontFamilies[fontFamily]" v-bind:root="scaleRoot" v-bind:ratio="activeRatio" v-bind:leading="leading"></preview>

            </div>
          </div>

        </div>
      </div>
    </div>

  </div>
</template>

<script>

import Scale from './components/Scale.vue'
import Preview from './components/Preview.vue'


export default {
  name: 'app',

  data () {
    return {
      scaleRoot: 16,
      fontFamily: 'nitti-grotesk',
      activeRatio: 1.333,
      leading: 1.5,
      ratios: {
        'minor-second':     { name: 'Minor second', val: 1.067 },
        'major-second':     { name: 'Major second', val: 1.125 },
        'minor-third':      { name: 'Minor third', val: 1.2 },
        'major-third':      { name: 'Major third', val: 1.25 },
        'perfect-fifth':    { name: 'Perfect fifth', val: 1.333 },
        'aug-forth':        { name: 'Aug. forth', val: 1.414 },
        'minor-sixth':      { name: 'Minor sixth', val: 1.5 },
        'golden-section':   { name: 'Golden section', val: 1.618 }
      },
      fontFamilies: {
        'nitti-grotesk':    { id: 'nitti-grotesk', name: 'Nitti Grotesk', val: 'nitti-grotesk' },
        'georgia':          { id: 'georgia', name: 'Georgia', val: 'Georgia' },
        'helvetica':          { id: 'helvetica', name: 'Helvetica Neue', val: 'Helvetica Neue' },
        'times-new-roman':          { id: 'times-new-roman', name: 'Times New Roman', val: 'Times New Roman' }
      }
    }
  },

  computed: {
  },

  methods: {
    increaseRoot () { this.scaleRoot++; },
    decreaseRoot () { this.scaleRoot--; }
  },

  components: {
    Scale,
    Preview
  }
}
</script>

<style lang="scss">

@import "./assets/scss/main.scss";

</style>
