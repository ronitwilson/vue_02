<template>
  <h1 :class="{ron: is_italized}" ref="my_header">  First vue app by {{ user }}</h1>
  <button @click="new_change_method"> Make the line italized</button>
  <div v-if="show_modal" >
    <Modal :prop_1_header="header_text" :prop2_text="para_text" :prop3_theme="theme1" @close="toggle_modal"/>
  </div>

  <button @click.alt="toggle_modal"> toggle modal (alt)</button>
</template>

<script>

import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: {Modal},
  data() {
    return {
      user: 'Ronit',
      is_italized: false,
      header_text: "Offer for my course!",
      para_text: "Only this month",
      theme1: "test_theme",
      show_modal: false
    }
    },
    methods: {
      change() {
        this.user = this.user + "_modified"
        this.is_italized = true
      },
      new_change_method() {
        console.log(this.$refs.my_header)
        this.$refs.my_header.classList.add('ron')
      },
      toggle_modal() {
        this.show_modal = !this.show_modal
      }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
}
h1.ron {
  font-style: italic;
}
</style>
