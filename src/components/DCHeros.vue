<template>
<div class="w-full flex">
  <div class="m-auto">  
   <h1 class="text-center text-4xl">DC Heros {{ herosCount }}</h1>
  <ul class="mt-3">
    <li class="flex justify-between text-2xl" v-for="(hero, index) in dcHeros" :key="hero.name">
      <div>{{ hero.name }} </div>
         <button @click="removeHero(index)" >x</button>
    </li>
  </ul>
  <form class="mt-10"
    @submit.prevent="addHero"
  >
    <input class="border rounded" type="text" v-model="newHero" placeholder="Type Hero Name here..." />
    <button class="border rounded bg-gradient-to-r from-red-500 to to-pink-500 text-sm text-white" type="submit">Add Hero</button>
  </form>
  </div>
</div>
</template>

<script>
export default {
    data() {
        return {
            newHero: "",
      dcHeros: [
          { name: "SuperGirl" },
        { name: "Flash" },
        { name: "Arrow" },
        { name: "Batman" },
        { name: "Superman" },
      ]
    };
  },
   methods:{
    addHero() {
      if (this.newHero !== '')
      this.dcHeros.unshift({ name: this.newHero });
      this.newHero = '';
    },
    removeHero(index){
      console.log(index)
     this.dcHeros = this.dcHeros.filter((hero,i) => i!=index )
    }
  },
  computed: {
    herosCount(){
      return this.dcHeros.length;
    },
  }
}
</script>

<style>

</style>