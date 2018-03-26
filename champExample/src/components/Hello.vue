<template>
  <div class="hello">
    <h1>{{count}}</h1>
    <input type="button" name="" value="++" @click="plus">
    <h1>{{realtimeplus}}</h1>
    <input type="number" name="" value="" v-model="num1">
    <input type="number" name="" value="" v-model="num2">
    <br><br>
    Name: <input type="text" v-model="inputName"><br>
    Email: <input type="text" v-model="inputEmail"><br>
    <button @click="addUser">Add</button>
    <hr>
    <table>
      <tr>
        <td>Name</td>
        <td>email</td>
        <td></td>
      </tr>
      <tr v-for="(user, index) in users">
        <td>{{ user.name }}</td>
        <td>{{ user.email }}</td>
        <td><button @click="deleteUser(index)">Delete</button></td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      count: 0,
      num1: 0,
      num2: 0,
      patt: /.+@\w+\..+/g,
      inputName: '',
      inputEmail: '',
      warning: '',
      users: [
        {
          name: 'nati',
          email: 'na@sellsuki.com'
        },
        {
          name: 'somchai',
          email: 'somchai@kmutnb.ac.th'
        }
      ]
    }
  },
  methods: {
    plus: function () {
      this.count ++
    },
    addUser: function () {
      if (this.inputName === '' || this.inputEmail === '') {
        return
      }
      var patt = /.+@\w+\..+/g
      if (patt.test(this.inputEmail)) {
        this.warning = ''
        this.users.push({
          name: this.inputName,
          email: this.inputEmail
        })
      } else {
        alert('Wrong email !!\nPlaese enter a valid email address.')
      }
    },
    deleteUser: function (index) {
      this.users.splice(index, 1)
    }
  },
  computed: {
    realtimeplus: function () {
      return this.num1 * 1 + this.num2 * 1
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
