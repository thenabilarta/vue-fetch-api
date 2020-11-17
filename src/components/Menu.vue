<template>
  <div>
    <button class="btn btn-primary" @click="click">Fetch</button>
  </div>
</template>

<script>
export default {
  name: "Menu",
  methods: {
    click: function() {
      this.$emit("termChange");
    },
  },
};
</script>

<style scoped></style>
