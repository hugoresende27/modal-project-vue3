<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <h1>My Vue App</h1>
  <p>{{ title }}</p>  
  <input type="text" ref="name">

  <hr>

  <p>Welcome</p>
  <button @click="handleClick">click me</button>

  <teleport to=".modals" v-if="showModal">
    <Modal :header="header" :text="text" theme="sale" @close="toogleModal"/>
  </teleport>  
  <button @click.shift="toogleModal">open modal  (shift)</button>

  <teleport to=".modals" v-if="showModalNew">
    <ModalNew theme="sale" @close="toogleModalNew">
        <template v-slot:links>
          <a href="#"><button>Sign Up </button></a>
          <br>
          <a href="#"><button>more info</button></a>
        </template>

      <h1>HelloWorld</h1>
          <!--<h1>HelloWorld22</h1>   -->
 
    </ModalNew>
  </teleport>  
  <button @click.right="toogleModalNew">open modal  (right)</button>



  <teleport to=".modals" v-if="showModalTwo">
    <ModalTwo :header="header" :text="text" theme="sale" @close="toogleModalTwo">
      <template v-slot:more_info>
          <p>info</p>
          <p>Sign up for updates</p>
        </template>
    </ModalTwo>
  </teleport>  
  <button @click="toogleModalTwo">open modal Two</button>

  
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Modal from './components/Modal.vue'
import ModalNew from './components/ModalNew.vue'
import ModalTwo from './components/ModalTwo.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
    Modal,
    ModalNew,
    ModalTwo,
  },
  data(){
    return {
      title: 'Hugão!',
      header: 'Sign up for the Giveway!!!',
      text: 'Grab your ninja swag for half price now !',
      showModal: false,
      showModalNew: false,
      showModalTwo: false,
    }
  },

  methods:{
    handleClick(){
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    },
    toogleModal() {
      this.showModal = !this.showModal
    },
    toogleModalNew() {
      this.showModalNew = !this.showModalNew
    },
    toogleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    } 
  }

}
</script>

<style>
  #app, .modals {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  h1 {
    border-bottom: 1px solid #ddd;
    display: inline-block;
    padding-bottom: 10px;
  }
</style>
