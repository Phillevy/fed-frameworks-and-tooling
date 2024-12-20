<script setup>
import Icon from '@/components/elements/Icon.vue'
defineProps(
    {
      title: {
        type: String,
        required: true
      },
      id: {
        type: String,
        required: false
      },
      className: {
        type: String,
        required: false
      },
      icon: {
        type: String,
        required: false
      }
    }
)
</script>

<template>
  <button
      :title="title"
      :class="className"
      :id="id"
  >
    <Icon :name="icon"  />
    {{ title }}
  </button>
</template>

<style scoped>
button
{
  display: inline-block;
  height: 2.5rem;
  padding: 0.25rem 0.75rem;
  color: #040138;
  text-align: center;
  font-size: 1rem;
  font-weight: normal;
  line-height: 2rem;
  letter-spacing: .1rem;
  text-decoration: none;
  white-space: nowrap;
  background-color: transparent;
  border-radius: 0.5rem;
  border-width: 0;
  border-style: solid;
  border-color: inherit;
  cursor: pointer;
  box-sizing: border-box;
}

button.disabled
{
  color: #898989;
}

button:focus
{
  color: #040138;
  background-color: #EAEAEA;
}

button.button--primary
{
  color: #FFF;
  background-color: #040138;
  border-color: #040138;
  border-width: 1px;
}

button.button--primary.disabled
{
  color: #898989;
  background-color: #F2F2F2;
  border-color: #EAEAEA;
}

button.button--primary:hover,
button.button--primary:focus
{
  color: #FFF;
  background-color: #3D3A6C;
  border-color: #3D3A6C;
}

button.button--secondary
{
  color: #000;
  background-color: #FFF;
  border-color: #898989;
  border-width: 1px;
}

button.button--secondary.disabled
{
  color: #898989;
  background-color: #F2F2F2;
  border-color: #D5D5D5;
}

button.button--secondary:hover,
button.button--secondary:focus
{
  color: #000;
  background-color: #F2F2F2;
  border-color: #898989;
}

</style>/