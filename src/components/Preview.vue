<template>
  <div class="preview">
    <h1 v-bind:style="h1Style">{{ family.name }}</h1>
    <p class="input__label text--muted">{{ family.name }} at {{ root }} px</p>
    <p v-bind:style="textStyle"><b>One morning, when Gregor Samsa woke from troubled dreams, he found himself transformed in his bed into a horrible vermin. He lay on his armour-like back, and if he lifted his head a little he could see his brown belly, slightly domed and divided by arches into stiff sections.</b></p>
    <p v-bind:style="textStyle">The bedding was hardly able to cover it and seemed ready to slide off any moment. His many legs, pitifully thin compared with the size of the rest of him, waved about helplessly as he looked. "What's happened to me?" he thought. It wasn't a dream. His room, a proper human room although a little too small, lay peacefully between its four familiar walls.</p>
  </div>
</template>

<script>
export default {
  name: 'preview',
  props: ['family', 'root', 'ratio', 'leading'],
  computed: {
    h1Style () {
      return 'font-family: '+ this.family.val +';'+
      'font-size: '+ this.root * (this.ratio * 3) / 16 +'rem;'
    },

    textStyle () {
      return 'font-family: '+ this.family.val +';'+
      'font-size: '+ this.root / 16 +'rem;'+
      'line-height: '+ this.leading
    },
  }
}
</script>

<style scoped>
</style>
