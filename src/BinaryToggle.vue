<template>
  <div class="flabel" v-on:click="change" :class="{disabled: disabled, dark: dark}">
    <div class="label"><slot></slot></div>
    <div class="on-off-holder"  :class="{sel: modelValue, large: large}">
      <div class="on-off-circle" ></div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    modelValue: Boolean,
    disabled: Boolean,
    large: Boolean,
    dark: Boolean
  },
  methods: {
    change() {
      if(!this.disabled){
        this.$emit('update:modelValue', !this.modelValue)
      }
    }
  }
}
</script>

<style>
  .flabel{
    display:inline-flex;
    margin:4px;
    border-radius:5px;
    padding:1px 3px;
    cursor:pointer;
    align-items:center;
  }

  .flabel.disabled{
    cursor:default;
  }

  .flabel:hover{
    background-color:#fff;
  }

  .flabel.dark:hover{
    background-color:#222;
  }

  .flabel.disabled:hover{
    background-color:#eee;
  }

   .flabel.disabled.dark:hover{
    background-color:#000;
  }

  .flabel .label{
    margin-right:5px;
  }
  .on-off-holder{
    background-color:#ccc;
    border-radius:7px;
    width:20px;
    height:12px;
    border:1px solid #ccc;
    position:relative;
  }

  .flabel.dark .on-off-holder{
    background-color:#444;
  }

  .on-off-holder.large{
    width:30px;
    height:19px;
    border-radius:9px;
    margin-left:5px;
  }

  .on-off-holder.sel{
    background-color:green;
    border-color:green;
  }

  .on-off-circle{
    position:absolute;
    top:1px;
    left:1px;
    width:10px;
    height:10px;
    border-radius:50%;
    background-color:#fff;
    margin:0;
    margin-right:0!important;
  }

  .large .on-off-circle{
    height:15px;
    width:15px;
  }

  .sel .on-off-circle{
    left:auto;
    right:1px;
  }
</style>