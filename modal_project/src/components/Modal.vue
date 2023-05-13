<template>
    <div class="backdrop" @click.self="toggle_modal">
        <div class="modal">
            <h1 :class="{test_theme: prop3_theme==='test_theme'}">{{ prop_1_header }}</h1>
            <p>
                {{prop2_text}}
                <slot></slot>
                <div class="actions">
                  <slot name="links"></slot>
                </div>
            </p>
        </div>
    </div>
</template>
<script>
export default {
    props: ['prop_1_header', 'prop2_text', 'prop3_theme'],
    methods: {
        toggle_modal() {
            this.$emit('close')
        }
    }
}
</script>
<style >
.modal {
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
  }
  .backdrop {
    top: 0;
    position: fixed;
    background: rgba(0,0,0,0.5);
    width: 100%;
    height: 100%;
  }

  .modal h1 {
    color: #03cfb4;
    border: none;
    padding: 0;
  }

  .modal h1.test_theme {
    color: #4a03cf;
    border: none;
    padding: 0;
  }

</style>
