
<template>
  <ul class="scale">
    <li v-for="num in scale">
      <b v-if="num === base">
        {{ num }}
      </b>
      <span v-else="num === base">
        {{ num }}
      </span>
    </li>
  </ul>
</template>

<script>

const lowNum = 4
const highNum = 7

export default {
  name: 'scale',
  props: ['base', 'ratio'],
  computed: {
    scale () {
      let list = new Array()

      // Loop down
      for( let i=0; i<lowNum; i++ ) {
        let low = Math.round( this.base / (this.ratio * (i+1)) )
        list.push( low )
      }

      // Add base
      list.reverse().push( this.base )

      // Loop up
      for( let i=0; i<highNum; i++ ) {
        let high = Math.round( this.base * this.ratio * (i+1) )
        list.push( high )
      }

      return list.reverse()
    }
  }
}

</script>
