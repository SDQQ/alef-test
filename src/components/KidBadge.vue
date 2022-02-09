<template>
<div class="badge">
  <p>{{kidItem.name}}, {{kidItem.age}} лет</p>
</div>
</template>

<script>
export default {
  name: "KidBadge",
  props:{
    kidItem:{
      type:Object,
      required:true
    }
  }
}
</script>

<style scoped>

.badge{
  padding: 10px 20px;
  margin: 20px 0;
  background: #F1F1F1;
  border-radius: 5px;
}
p{
  font-weight: bold;
  font-size: 16px;
  line-height: 24px;
}
</style>