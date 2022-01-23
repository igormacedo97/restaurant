<template>
  <div class="loading"></div>
</template>

<script>
export default {
  name: "Loading",
};
</script>

<style lang="less" scoped>
.loading {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  border: 3px solid #ffe4a1; // @light-yellow não funcionando no navegador
  border-top-color: @yellow;
  animation: spin 1s linear infinite;
  margin: auto;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}
</style>
