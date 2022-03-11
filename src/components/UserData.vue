<template>
    <h3>{{ userName }}</h3>
    <h4>{{ age }}</h4>
</template>
<script>
import { computed } from 'vue';
export default {
    props: ['firstName','lastName', 'age'],
    setup(props){
        const uName = computed(function() {
            return props.firstName + " "+ props.lastName
        })
            return { userName: uName};

    }

    // computed:{
    //     userName(){
    //         return this.firstName+ " "+ this.lastName;
    //     }
    // }
}
</script>