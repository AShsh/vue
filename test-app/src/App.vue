<template>
  <div id="app">
    <AddUser :addUser='addUser'/>
    <UserList :userList='userList' />
  </div>
</template>

<script>
import AddUser from '@/components/AddUser'
import UserList from '@/components/UserList'
export default {
  name: 'App',
  data () {
    return {
      userList: localStorage.getItem('userList') ? JSON.parse(localStorage.getItem('userList')) : []
    }
  },
  components: {
    AddUser: AddUser,
    UserList: UserList
  },
  methods: {
    addUser (data) {
      this.userList.push(data.userData)
      localStorage.setItem('userList', JSON.stringify(this.userList))
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
