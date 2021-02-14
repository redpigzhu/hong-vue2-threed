<template>
   <div>
    <!-- <h2> {{objPath}} </h2> -->
    <model-obj  :backgroundAlpha="0"
        @on-load="onLoad" :src="objPath" :mtl="mtlPath" ></model-obj>
   </div>
</template>

<script>
  import { ModelObj } from 'vue-3d-model'

  export default {
    name: 'threed-view',
    components: { ModelObj },
    props: {
      objPath: {
        type: String,
        required: true
      },
      mtlPath: {
        type: String,
        required: true
      }
    }, 
    data() {
      return {
        loading: true
     
      };
    },
    methods: {
      onLoad() {
        this.loading = false;
      },
    }
  };

  </script>
  