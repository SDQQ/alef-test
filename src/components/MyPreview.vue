<template>
  <div class="preview">
    <template v-if="formData.name.length && formData.age.length">
      <h2>Персональные данные</h2>
      <p>{{ formData.name }}, {{ formData.age }} лет</p>
      <h4>Дети</h4>
      <template v-if="formData.kids.length">
        <kid-badge
            :kid-item="kid"
            v-for="kid in formData.kids"
        ></kid-badge>
      </template>
      <p class="no-kids" v-else>Отсутствуют</p>

    </template>
    <div v-else>
      <h2>
        Пока ничего нету, проверьте правильность заполненной формы и сохраните её.
      </h2>
    </div>


  </div>
</template>

<script>
import KidBadge from "./KidBadge.vue";

export default {
  name: "MyPreview",
  components: {KidBadge},
  props: {
    formData: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.preview {
  display: flex;
  flex-direction: column;
  margin: 30px auto 30px auto;
  max-width: 300px;
}

h2 {
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
  margin-bottom: 20px;
}

p {
  font-weight: bold;
  margin-bottom: 60px;
  font-size: 16px;
  line-height: 24px;
}
.no-kids{
  font-weight: 400;

  margin-top: 20px;
}
</style>