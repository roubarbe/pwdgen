<template>
  <div class="container text-center">
    <div class="row title mt-5">
      <h1 class="display-1">Un mot de passe?</h1>
    </div>
    <div class="row justify-content-center mb-3 mt-3">
      <div class="row justify-content-center">
        <div class="col-2">
          <label for="numPwd" class="form-label">Combiens?</label>
          <input type="number" id="numPwd" class="form-control-sm form-control" min="1" max="99" v-model="pwdAmount">
        </div>
        <div class="col-2">
          <label for="lenPwd" class="form-label">Long comment?</label>
          <input type="number" id="lenPwd" class="form-control-sm form-control" min="8" max="16" v-model="pwdLen">
        </div>
      </div>
      <div class="row justify-content-center mt-3">
        <div class="col-auto">
          <button v-if="pwdAmount == 1" class="btn btn-primary btn-lg" @click="this.pwdGenerate()">Génère-moi {{pwdAmount}} mot de passe</button>
          <button v-else class="btn btn-primary btn-lg" @click="this.pwdGenerate()">Génère-moi {{pwdAmount}} mots de passe</button>
        </div>
        <div class="col-auto">
          <button class="btn btn-secondary btn-lg" @click="this.pwdClear()">Effacer</button>
        </div>
        
      </div>
      
    </div>
    <Pwdgen ref="pwdgenerator"></Pwdgen>
    
    
  </div>
</template>

<script>
// import { ref } from 'vue'
import Pwdgen from './pwdgen/pwdgen.vue'

export default {
  name: 'Home',
  components: {
    Pwdgen
  },
  data: function(){
    return {
      pwdAmount: 1,
      pwdLen: 16
    }
  },
  methods:{
    pwdGenerate: function(){
      this.$refs.pwdgenerator.generate(this.pwdAmount, this.pwdLen)
    },

    pwdClear: function(){
      this.$refs.pwdgenerator.clear();
    }
  }
}
</script>

<style lang="scss">

.title{
  h1{
    color: var(--main-color)
  }
}

</style>
