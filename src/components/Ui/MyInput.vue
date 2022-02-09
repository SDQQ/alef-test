<template>
  <div>
    <label :for="label">
      {{label}}
    </label>
    <input
        @change="update"
        :id="label"
        :type="inputType"
        :placeholder="inputPlaceholder"
        required
    >
  </div>
</template>

<script>
export default {
  name: "MyInput",
  emits:['update:modelValue'],
  methods:{
    update(e){
      this.$emit('update:modelValue', e.target.value)
    }
  },
  props:{
    label:{
      type:String,
      required:true,
    },
    inputType:{
      type:String,
      default:'text'
    },
    inputPlaceholder:{
      type:String,
    },
  }
}
</script>

<style scoped>
div{
  padding: 6px 16px;
  display: flex;
  flex-direction: column;
  min-height: 56px;
  border: 1px solid #E8E8E8;
  margin: 10px 0 10px 0;
}
input{
  border: none;
  font-size: 14px;
  line-height: 24px;
}
label{
  color: #8D8D8D;
  font-size: 13px;
  line-height: 15.85px;
}
input,label{
  outline: none;
}
</style>