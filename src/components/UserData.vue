<template>
    <div>
        <h3>{{ userName }}</h3>
        <h4>{{ age }}</h4>
    </div>
</template>
<script>
import { computed, 
         inject, 
         onBeforeMount, 
         onMounted, 
         onBeforeUpdate, 
         onUpdated, 
         onBeforeUnmount, 
         onUnmounted 
      } from 'vue';
export default {
    props: ['firstName','lastName'],
    setup(props){
        const uName = computed(function() {
            return props.firstName + " "+ props.lastName
        })
        
        const age = inject('userAge');

        onBeforeMount(function(){
            console.log('onBeforeMount');
        })

        onMounted(function(){
            console.log('onMounted');
        })

        onBeforeUpdate(function(){
            console.log('onBeforeUpdate');
        })

        onUpdated(function(){
            console.log('onUpdated');
        })

        onBeforeUnmount(function(){
            console.log('onBeforeUnmount');
        })

        onUnmounted(function(){
            console.log('onUnmounted');
        })

        // context.emit(); // this.$emit('save-data', 1);

        return { userName: uName, age};

    },

  

    // computed:{
    //     userName(){
    //         return this.firstName+ " "+ this.lastName;
    //     }
    // }
}
</script>