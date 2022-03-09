<template>
  <section class="container">
    <h2>{{ user.name }}</h2>
    <h3>{{ user.age }}</h3>
    <button @click="setAge">Submit</button>
    <div>
      <input type="text" placeholder="First Name"/>
      <input type="text" placeholder="Last Name"/>
    </div>
  </section>
</template>

<script>
// import { ref } from 'vue';
import { reactive } from 'vue';

export default {
  setup() {
      // const uName = ref('Maximillan');
      // const uAge = ref(31);
      // setTimeout(function() {
      //   uName.value = 'Max';
      // },2000)
      // return { userName: uName, age: uAge}
    //  const uAge = ref(31);
      const user = reactive({
        name: 'Maxmillan',
        age: 31
      })

      function setNewAge() {
        user.age = 20;
      }
      // console.log(isRef(uAge.value));  // false
      // console.log(isReactive(user.name)); // false

      // console.log(isRef(uAge));  // True
      // console.log(isReactive(user)); // True

      // const userRefs = toRefs(user);
      // console.log(isRef(userRefs.name)); // true (convert reactive to refs)

      // setTimeout(function(){
      //   user.name = "Max",
      //   user.age = 34
      // },2000)

      return { user: user, setAge: setNewAge}
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