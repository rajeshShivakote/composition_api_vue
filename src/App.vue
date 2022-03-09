<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
    <button @click="setAge">Submit</button>
    <div>
      <input type="text" placeholder="First Name" @input="setFirstName"/>
      <input type="text" placeholder="Last Name" @input="setLastName"/>
    </div>
  </section>
</template>

<script>
// import { ref } from 'vue';
import { ref, computed } from 'vue';

export default {
  setup() {
      // const uName = ref('Maximilian');
      const firstName = ref('');
      const lastName = ref('');
      const uAge = ref('1')

      const uName = computed(function(){
         return firstName.value + ' ' + lastName.value;
      })
      let setNewAge = () =>{
        uAge.value = 33;
      }  

      function setFirstName() {
        firstName.value = event.target.value;
      }

      function setLastName() {
        lastName.value = event.target.value;
      }
      return {
        userName: uName, 
        age: uAge, 
        setAge: setNewAge, 
        setFirstName: 
        setFirstName, 
        setLastName: setLastName
        }
  }
  // data() {

  //   return {
  //     userName: 'Maximilian',
  //     age: 32
  //   };
  // },
  // methods: {
  //   setNewAge() {
  //     this.age = 32
  //   }
  // },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>