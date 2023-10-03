<template>
  <div class="home">
    <title>Home page</title>
    <h1>this is a home page</h1>
    <h2 v-if="!showlist">لطفا صبر کنید</h2>
    <div class="div" v-for="i in list">
        <nuxt-link :to="'/food/' + i.id">{{i.title}}</nuxt-link>
        <br>
        <br>
        <a :href="'/food/' + i.id">{{i.title}}</a>
        <br>
        <br>
        <hr>
    </div>

    <Home1Comp></Home1Comp>

  </div>
</template>

<script>
import axios from "axios"
import { onMounted , ref} from "vue";
export default {
  setup() 
  {
    const list = ref([])
    const showlist = ref(false)

    onMounted(() => {
        axios.get('https://fakestoreapi.com/products').then((response)=>{
            list.value = response.data;
            showlist.value = true
        })
    })

    return{
        list,
        showlist
    }
  },
};
</script>
