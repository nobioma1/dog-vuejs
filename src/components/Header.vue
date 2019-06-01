<template>
  <div class="header">
    <h1>Random Dog Viewer 🐶</h1>
  </div>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style scoped>
  .header {
    position: fixed;
    color: white;
    background-color:dimgray;
    top: 0;
    left: 0;
    width: 100%;
  }

  .header h1 {
    text-align: center;
    font-size: 24px;
  }
</style>
