<template>
  <button @click="onClick()" v-bind:style="{background:color}"
          class="btn">{{ text }}
  </button>
</template>
<script>
export default {
  name: 'Button',
  props: {
    text: String,
    color: String
  },
  methods: {
    onClick() {
      console.log("Clicked the button")
    }
  }
}
</script>