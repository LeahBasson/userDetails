<template>
  <form class="container">
   <div><input type="text" placeholder="First name" required v-model="firstName"><span v-show="!firstName.length">*</span></div>
   <div><input type="text" placeholder="Last name" required v-model="lastName"><span v-show="!lastName.length">*</span></div>
   <div><input type="text" placeholder="Gender" required v-model="gender" :class="{male: lowerCaseGender == 'male',
      female: lowerCaseGender == 'female'
    }"><span v-show="!gender.length">*</span></div>
    <textarea output readonly></textarea>
    <button @click.prevent="userInfo">Display</button>
  </form>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return{
      firstName: '',
      lastName: '',
      gender:''
    }
  },

  methods: {
    userInfo() {
      document.querySelector('[output]').textContent = 
      `
        First name: ${this.firstName}
        Last name: ${this.lastName}
        Gender: ${this.gender}
      `
    }
  },

  computed: {
    lowerCaseGender(){
      return this.gender.toLowerCase()
    }

  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container{
  display: grid;
  gap: .2rem;
  width: 30rem;
  margin-inline: auto;
  & input{
    text-align: center;
  }
}

.male{
  border: 2px solid blue;
}

.female{
  border: 2px solid pink;
}

span{
  color: red;
}

input{
  width: 29rem;
}

</style>
