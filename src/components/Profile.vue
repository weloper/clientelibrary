<template>
<v-layout row wrap>
  <navbar></navbar>
  <div class="container" id="profile">
    <div class="jumbotron mt-5">
      <div class="col-sm-8 mx-auto">
        <h1 class="text-center">PROFILE</h1>
      </div>
      <table class="table col-md-6 mx-auto">
        <tbody>
          <tr>
            <td>Fist Name</td>
            <td>{{first_name}}</td>
          </tr>
          <tr>
            <td>Last Name</td>
            <td>{{last_name}}</td>
          </tr>
          <tr>
            <td>Email</td>
            <td>{{email}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</v-layout>
</template>

<script>
import jwtDecode from 'jwt-decode'
import NavBar from './NavBar'

export default {
  data () {
    const token = localStorage.usertoken
    const decoded = jwtDecode(token)
    return {
      first_name: decoded.identity.first_name,
      last_name: decoded.identity.last_name,
      email: decoded.identity.email
    }
  },
  components:{
    'navbar': NavBar
  }
}
</script>

<style>
#profile table, h1{
  color:lightsalmon
}
</style>