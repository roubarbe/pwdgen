<template>
    <div class="row mb-3" v-if="genPwds.length > 0">
        <input 
            type="text" 
            v-for="password in genPwds" 
            :key="password" 
            class="form-control form-control-lg text-center mb-1 passwords-item" 
            :value="password" 
            readonly
        >
    </div>
</template>

<script>

export default {
  name: 'Pwdgen',
  components: {
  },
  data: function(){
      return {
          genPwds: []
      }
  },
  methods: {
    generate(pwdAmount, pwdLen){
        let i;
        for(i = 0; i < pwdAmount; i++){
            let password = "";
            let validPwdRegex = new RegExp("(.*[a-z].*)(.*[A-Z].*)(.*\\d.*)(.*\\W.*)");

            while(!validPwdRegex.test(password)){
                password = this.generateSinglePassword(pwdLen);
            }

            this.genPwds.push(password);
        }
    },

    generateSinglePassword(pwdLen){
        let password = "";
        let validChars = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXY0123456789!@#$%?&*"
        let e;
        for(e = 0; e < pwdLen; e++){
            let random = Math.floor(Math.random() * validChars.length);
            let randomChar = validChars[random];
            password += randomChar;
        }

        return password;
    },

    clear(){
        this.genPwds = [];
    }
  }
}
</script>

<style lang="scss">
</style>
