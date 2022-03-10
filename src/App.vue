<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
    <button @click="setAge">Submit</button>
    <div>
      <input type="text" placeholder="First Name" v-model="firstName"/>
      <input type="text" placeholder="Last Name" v-model="lastName"/>
    </div>
  </section>
</template>

<script>
// import { ref } from 'vue';
import { ref, computed, watch } from 'vue';

export default {
  setup() {
      // const uName = ref('Maximilian');
      const firstName = ref('');
      const lastName = ref('');
      const uAge = ref('1')

      
      const uName = computed(function(){
         return firstName.value + ' ' + lastName.value;
      })

      watch([uAge, uName], function(newValue, oldValue) {
          console.log("Old Vakue ",oldValue[0]);
          console.log("New Value ",newValue[0]);
           console.log("Old name ",oldValue[1]);
          console.log("New name ",newValue[1])
      })
      let setNewAge = () =>{
        uAge.value = 33;
      }  

      
      return {
        userName: uName, 
        age: uAge, 
        setAge: setNewAge, 
        firstName,
        lastName, 
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