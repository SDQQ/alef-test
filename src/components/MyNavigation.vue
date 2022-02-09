<template>
  <nav>
    <img src="/Logo.svg" alt="Logo">
    <ul>
      <li>
        <button @click="updCurrentComponent('MyForm')"
                type="button"
        >Форма
        </button>
      </li>
      <li>
        <button @click="updCurrentComponent('MyPreview')"
                type="button"
        >Превью
        </button>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "MyNavigation",
  methods: {
    updCurrentComponent(component) {
      this.$emit('update:modelValue', component)
    }
  }
}
</script>

<style scoped>
nav {
  position: relative;
  display: flex;
  min-height: 76px;
  align-items: center;
  border-bottom: 1px solid #E8E8E8;
}


img {
  padding: 5px 41px;
  width: 175px;
  height: 40px;
  cursor: pointer;
  margin-left: 51px;
}

ul {
  margin: 0 auto;
  list-style: none;
  display: flex;
  font-size: 14px;
  line-height: 24px;
  gap: 24px;
}

button {
  padding: 5px;
  color: #8D8D8D;
  text-decoration: none;
  background-color: transparent;
  border: none;
  cursor: pointer;
}
</style>