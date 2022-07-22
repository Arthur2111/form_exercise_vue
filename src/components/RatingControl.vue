<template>
  <!-- creating custom control component -->
  <!-- notive when selecting any of the buttons below the form will automatically submit (givent the component has been inserted to a form) -->
  <!-- hence we give each button a type='button' so that it is not the default of submit -->
  <ul>
    <li :class="{active: modelValue === 'poor'}"><button type="button" @click="activate('poor')">Poor</button></li>
    <li :class="{active: modelValue === 'average'}"><button type="button" @click="activate('average')">Average</button></li>
    <li :class="{active: modelValue === 'great'}"><button type="button" @click="activate('great')">Great</button></li>
  </ul>
</template>

<script>
export default {
    // when we assign v-model to a component it the child component takes a modelValue prop made by Vue and an event to be emitted update:modelValue
    props: ['modelValue'],
    emits: '[update:modelValue]',
    // data() {
    //     return {
    //         // the idea is that when we select an option the active option should change to the button selected
    //         activeOption: this.modelValue
    //     }
    // },
    computed: {
        activeOption() {
            return this.modelValue
        }
    },
    methods: {
        activate(option) {
            this.$emit('update:modelValue', option)
        }
    }
}





// the idea is that we want to add a style to the selected button








</script>

<style scoped>
/* we will only add the active class to the li that is selected */

.active {
  border-color: purple;
}
.active button {
  color: purple;
}

ul {
  list-style: none;
  margin: 0.5rem 0;
  padding: 0;
  display: flex;
}

li {
  margin: 0 1rem;
  border: 1px solid #ccc;
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

button {
  font: inherit;
  border: none;
  background-color: transparent;
  cursor: pointer;
}
</style>


