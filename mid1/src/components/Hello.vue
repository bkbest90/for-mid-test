<template>
  <div class="hello">
    <h1>phoneBook</h1>
    <table align="center">
      <tr>
        <td>#</td>
        <td width="200px">Name</td>
        <td width="200px">เบอร์โทร</td>
        <td width="200px">email</td>
        <td width="200px">Delete</td>
      </tr>
      <tr v-for="(user, index) in users" align="center">
        <td>{{index+1}}</td>
        <td>{{ user.name }}</td>
        <td>{{ user.number }}</td>
        <td>{{ user.email }}</td>
        <td ><button @click="deleteUser(index)">Delete</button></td>
      </tr>
    </table>
    <br><br><hr>
    ชื่อ: <input type="text" v-model="inputName">
    เบอร์โทร: <input type="text" v-model="inputNumber">
    Email: <input type="text" v-model="inputEmail">
    <button @click="addUser">Add</button>


  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      inputName: '',
      inputNumber: '',
      inputEmail: '',
      users: [
      ]
    }
  },
  methods: {
    addUser: function () {
      if (this.inputName === '' || this.inputEmail === '') {
        return
      }
      var pattMail = /.+@\w+\..+/g
      var pattNumber = /^0\d{2}-\d{3}-\d{4}$/g
      var mailMatch = pattMail.test(this.inputEmail)
      var numberMatch = pattNumber.test(this.inputNumber)
      if (mailMatch) {
        if (numberMatch) {
          this.users.push({
            num: this.count,
            name: this.inputName,
            number: this.inputNumber,
            email: this.inputEmail
          })
        } else {
          alert('Wrong phone number !!\nPlaese enter a valid phone number.')
        }
      } else {
        alert('Wrong email !!\nPlaese enter a valid email address.')
      }
    },
    deleteUser: function (index) {
      this.users.splice(index, 1)
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
</style>
