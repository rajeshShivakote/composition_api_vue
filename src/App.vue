<template>
  <section class="container">
    <!-- <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3> -->
    <user-data :first-name="firstName" :last-name="lastName" :userName="userName"></user-data>
    <button @click="setAge">Submit</button>
    <div>
      <input type="text" placeholder="First Name" v-model="firstName"/>
      <input type="text" placeholder="Last Name" ref="lastNameInput"/>
      <button @click="setLastName">Set LastName</button>
    </div>
  </section>
</template>

<script>
// import { ref } from 'vue';
import { ref, computed, watch, provide } from 'vue';
import UserData from '@/components/UserData'
export default {
  components:{
    UserData
  },
  setup() {
      // const uName = ref('Maximilian');
      const firstName = ref('');
      const lastName = ref('');
      const lastNameInput = ref(null);
      const uAge = ref('1')

      provide('userAge', uAge);
      
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

      function setLastName() {
        lastName.value = lastNameInput.value.value;
      }

      
      return {
        userName: uName, 
        age: uAge, 
        setAge: setNewAge, 
        firstName,
        lastName, 
        lastNameInput,
        setLastName
        }
  },
   
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
  //  provide() {
  //       return { age: }
  //   }
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