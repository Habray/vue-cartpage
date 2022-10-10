<template>
  <div class="about">
    <h1>Adding Animals ({{lengthOfList}})</h1>

    <div>
      <input v-model="animalname" placeholder="Animal Name" />
      <button @click="submitbtn">Submit</button>
    </div>

    <ul>
      <li v-for="ani,index in animalslist" :key="index">{{ ani }}</li>
    </ul>

    <h1>Searching Animal</h1>

    <div>
      <input v-model="animalnamesearch" placeholder="Animal Name" />
    </div>

    <!-- <ul>
      <li v-for="eachani in animalslist">
        <p v-if="eachani.toUpperCase().indexOf(animalnamesearch.toUpperCase()) > -1">{{ eachani }}</p>
      </li>
    </ul> -->

    <ul>
      <li>{{animalsearch}}</li>
    </ul>
  </div>
</template>

<script setup>
// import { computed } from "@vue/reactivity";
import { computed } from "@vue/reactivity";
import { ref } from "vue";

var animalslist = ref([]);
var animalnamesearch = ref('');
var animalname = ref();
var eachani = ref('');

function submitbtn() {
  // alert(animalslist.value);
  animalslist.value.push(animalname.value);
  animalname.value = "";
}

const lengthOfList = computed({
  get() {
    return animalslist.value.length;
  }
})

const animalsearch = computed({
  get() {
    for(eachani in animalslist){
      if(eachani.indexOf(animalnamesearch.value) > -1){
        return eachani;
      }
    }
  }

  // set() {
    
  // }
})


// watch(alphabets, (newValue) => {
// numberOfString.value = newValue.length
// })

</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    /* display: flex; */
    align-items: center;
  }
}
</style>
