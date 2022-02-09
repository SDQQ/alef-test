<template>
  <div class="container">
    <my-navigation v-model="currentComponent"></my-navigation>
    <component
        @submitForm="setForm"
        :is="currentComponent"
        :formData="formData"
    ></component>
  </div>
  <my-footer></my-footer>
</template>

<script>
import MyNavigation from "./components/MyNavigation.vue";
import MyForm from "./components/MyForm.vue";
import MyFooter from "./components/MyFooter.vue";
import MyPreview from "./components/MyPreview.vue";

export default {
  components: {MyFooter, MyForm, MyNavigation, MyPreview},
  data() {
    return {
      formData: {
        name: '',
        age: '',
        kids: []
      },
      currentComponent: 'MyForm'
    }
  },
  methods: {
    setForm(form) {
      this.formData = form
      this.currentComponent = 'MyPreview'
    }
  }
}
</script>

<style>


</style>