<template>
    <div class="cloth-view">
        <div class="cloth-view__select">
         <label for="selectCloth"><strong>select Cloth to view </strong></label>
          <select id="selectCloth" v-model="selectedClothName" @change="changeSelection">
              <option :value="acloth.name" v-for="(acloth, index) in user.cloths" :key="index">
                  {{ acloth.name }}
              </option>
          </select>
          </div>
      <ThreedView :objPath="selectedCloth.src" :mtlPath="selectedCloth.mtl" :key="componentKey" />
     </div>
</template>

<script>
  import ThreedView from "./components/ThreedView";

  export default {
    name: 'App',
    components: { ThreedView },
    data() {
      return {
        componentKey: 0,
        selectedClothName: 'hoodie',
        selectedCloth: {
          src: "https://eddiekusel.github.io/hoodie.obj",
          mtl : "https://eddiekusel.github.io/hoodie.mtl"
        },
        user:{
          id:1,
          username:'whoami',
          firstName:"who",
          lastName:'am',
          email:'whoami@gmail.com',
          isAdmin: true,
          cloths :[
          {id: 1, name: "hoodie"},
          {id: 2, name: "knit"}
        ]

      }
    }
    },
    methods: {
      changeSelection()
      {
        this.selectedCloth.src = `https://eddiekusel.github.io/${this.selectedClothName}.obj`;
        this.selectedCloth.mtl = `https://eddiekusel.github.io/${this.selectedClothName}.mtl`;
        this.componentKey += 1;  
        console.log(this.selectedCloth );
      }
    }
  };
  </script>

<style>
.cloth-view {
  display: grid;
  grid-template-columns: 1fr 3fr;
  width: 100%;
  padding: 50px 5%;
  text-align: left;
}
</style>