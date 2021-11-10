<template>
<div class="users-wrapper">
  <table class="table">
    <thead class="thead-dark">
      <tr>
        <th>번호</th>
        <th>이름</th>
        <th>전화번호</th>
        <th>이메일</th>
      </tr>
    </thead>
    <tbody>
    <tr v-for=" v in users" :key="v.id" >
      <th>{{v.id}}</th>
        <th>{{v.name}}</th>
        <th>{{v.phone}}</th>
        <th>{{v.email}}</th>
    </tr>
    </tbody>
  </table>
</div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Users',
  data () {
    return {
      users: []
    }
  },
  async created () {
    const url = 'https://jsonplaceholder.typicode.com/users'
    const { data } = await axios.get(url)
    this.users = data
    console.log(this.users)
  }
}
</script>

<style lang="scss" scoped>
 .users-wrapper {
   width: 90%;
   max-width: 720px;
   margin: 2em auto;
   overflow-y :auto;
 }
</style>
