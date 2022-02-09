<template>
  <footer>
    <p>all rights reserved</p>
  </footer>
</template>

<script>
export default {
  name: "MyFooter"
}
</script>

<style scoped>
footer {
  width: 100vw;
  height: 76px;
  position: absolute;
  bottom: 0;
  background-color: #FAFAFA;
  display: flex;
  justify-content: center;
  align-items: center;
}

p {
  font-size: 13px;
  line-height: 16px;
}
</style>