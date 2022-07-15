<template>
  <div class="home">
    <h1>Home</h1>
    <div>
      <p>My name is {{name}}.I am {{age}} years old.</p>
    <button @click="changeName">Change Name</button>
    <button @click="increaseAge">Increase Age</button>
    </div>
    <br>
    <hr>
    <br>

    <input type="text" v-model="search">
    <p>Search items - {{search}}</p>
    <div v-for="person in filterPersons" :key="person">
            {{person}}
    </div>

     
  </div>
</template>

<script>
import { ref } from '@vue/reactivity'
import { computed } from '@vue/runtime-core';
export default {
  setup(){
    let name = ref("Kyaw Kyaw");
    let age = ref(20);

    let changeName=()=>{
      name.value="Mg Mg"
    };

    let increaseAge=()=>{
      age.value++
    };


    let persons=ref(['Zaw Zaw','Mg Mg','Su Su','Tun Tun']);

    let search = ref("");

    let filterPersons=computed(()=>{
      return persons.value.filter((person)=>{
        return person.includes(search.value)
      })
    })

    return{name,age,changeName,increaseAge,persons,search,filterPersons};
  }
}
</script>
