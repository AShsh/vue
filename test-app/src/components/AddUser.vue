<template>
  <div>
    <form>
      <input type="text" v-model='firstName' :class="{'has-error': errors.has('firstName') }" v-validate="firstName" data-vv-rules="required|alpha" placeholder="firstName" >
      <input type="text" v-model='lastName' :class="{'has-error': errors.has('lastName') }" v-validate="lastName" data-vv-rules="required|alpha" placeholder="lastName" >
      <input type="email" v-model='email' v-validate="email" data-vv-rules="required|email" :class="{'has-error': errors.has('email') }" placeholder="email" >
      <input type="text" v-model.number='age' :class="{'has-error': errors.has('age') }" v-validate="age" data-vv-rules="numeric" placeholder="age">
      <input type="text" v-model='skype' :class="{'has-error': errors.has('skype') }" v-validate="skype" data-vv-rules="alpha|min:4|max:10" placeholder="skype" >
      <input type="submit" value="add user" :disabled="errors.any()"  @click.prevent='add' >
    </form>
  </div>
</template>

<script>

export default {
  name: 'AddUser',
  props: {
    'addUser': {
      type: Function,
      required: true
    }
  },
  data () {
    return {
      userData: {},
      firstName: '',
      lastName: '',
      email: '',
      age: '',
      skype: ''
    }
  },
  methods: {
    add () {
      this.addUser({
        userData: {
          firstName: this.firstName,
          lastName: this.lastName,
          email: this.email,
          age: this.age,
          skype: this.skype
        }
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
input {
  display: block;
  margin: 0 auto;
}

.has-error {
  background: rgba(2,2,2,.3);
}
</style>
