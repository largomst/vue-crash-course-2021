<template>
  <button class="btn" @click="onClick()" v-bind:style="{ background: color }">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: String,
    color: String,
  },
  methods: {
    onClick: function () {
      this.$emit("btn-click");
    },
  },
};
</script>

<style scoped>
</style>