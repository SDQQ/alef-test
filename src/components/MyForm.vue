<template>
  <form @submit.prevent="submitForm">
    <h2>Персональные данные</h2>
    <my-input
        v-model="formData.name"
        label="Имя"
        input-type="text"
        input-placeholder="Введите имя"
    />
    <my-input
        v-model="formData.age"
        label="Возраст"
        input-type="number"
        input-placeholder="Введите возраст"
    />
    <div class="kids-title">
      <h2>Дети (макс. 5)</h2>
      <button v-if="formData.kids.length < 5"
              @click="addKid"
              class="kid-add"
              type="button"
      >Добавить ребенка
      </button>
    </div>

    <template v-if="formData.kids.length">
      <my-kid
          v-model="formData.kids[index]"
          @removeKid="removeFormKid"
          :key="kid.id"
          :kid="kid"
          v-for="(kid,index) in formData.kids"></my-kid>
    </template>
    <button
        class="form-save"
        type="submit"
    >Сохранить
    </button>
  </form>
</template>

<script>
import MyInput from "./Ui/MyInput.vue";
import MyKid from "./MyKid.vue";
import {v4 as uuidv4} from 'uuid';

export default {
  name: "MyForm",
  components: {MyInput, MyKid},
  data() {
    return {
      formData: {
        name: '',
        age: '',
        kids: [],
      }
    }
  },
  methods: {
    addKid() {
      if (this.formData.kids.length < 5) {
        this.formData.kids.push({name: '', age: '', id: uuidv4()})
      }
    },
    removeFormKid(id) {
      this.formData.kids = this.formData.kids.filter(kid => kid.id !== id)
    },
    submitForm() {
      this.$emit('submitForm', this.formData)
    }
  }
}
</script>

<style scoped>
form {
  margin: 30px auto;
  width: 650px;
  padding: 15px;
}

h2 {
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
}

.kids-title {
  display: flex;
  justify-content: space-between;
  min-height: 50px;
  align-items: center;
}

.kid-add {
  cursor: pointer;
  position: relative;
  max-width: 204px;
  min-height: 44px;
  font-size: 14px;
  line-height: 24px;
  color: var(--main-blue);
  background-color: transparent;
  padding: 10px 20px 10px 40px;
  border: 2px solid var(--main-blue);
  border-radius: 100px;
}

.kid-add::before {
  top: 50%;
  transform: translateY(-50%);
  left: 18px;
  content: '';
  position: absolute;
  width: 16px;
  height: 2px;
  border-radius: 20px;
  background-color: var(--main-blue);
}

.kid-add::after {
  top: 50%;
  transform: translateY(-50%);
  left: 25px;
  content: '';
  position: absolute;
  width: 2px;
  height: 16px;
  border-radius: 20px;
  background-color: var(--main-blue);
}

.form-save {
  cursor: pointer;
  margin-top: 30px;
  background-color: var(--main-blue);
  color: white;
  border: none;
  border-radius: 100px;
  padding: 10px 20px;
}

</style>