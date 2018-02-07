<template>
  <table>
    <tr>
      <td>First Name</td>
      <td>Last Name</td>
      <td>Email</td>
      <td>Age</td>
      <td>Skype</td>
    </tr>
    <tr v-for="item in userList" v-bind:key="item.id">
      <td>{{item.firstName}}</td>
      <td>{{item.lastName}}</td>
      <td>{{item.email}}</td>
      <td>{{item.age}}</td>
      <td>{{item.skype}}</td>
    </tr>
  </table>
</template>

<script>
export default {
  name: 'UserList',
  props: {
    userList: {
      type: Array
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
table {
  margin: 0 auto;
  border-spacing: 0;
  border-collapse: collapse;
}

td {
   border: 1px solid black;
}

td {
  padding: 8px;
}
</style>
