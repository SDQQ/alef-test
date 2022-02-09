<template>
  <div class="kids">
    <my-input
        v-model="kid.name"
        label="Имя"
        input-type="text"
        input-placeholder="Введите имя"
    />
    <my-input
        v-model="kid.age"
        label="Возраст"
        input-type="number"
        input-placeholder="Введите возраст"
    />
    <button
        @click="remove(kid.id)"
        class="kid-remove"
        type="button"
    >Удалить
    </button>
  </div>
</template>

<script>
import MyInput from "./Ui/MyInput.vue";

export default {
  components: {MyInput},
  name: "MyKid",
  emits: ['removeKid',],
  methods: {
    remove(id) {
      this.$emit('removeKid', id)
    }
  },
  props: {
    kid: {
      type: Object
    },

  },
}
</script>

<style scoped>
.kid-remove {
  cursor: pointer;
  color: var(--main-blue);
  font-size: 14px;
  line-height: 24px;
  background-color: transparent;
  border: none;

}

.kids {
  display: flex;
  justify-content: space-between;
}
</style>