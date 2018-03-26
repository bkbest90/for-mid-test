<template>
  <div class="hello">
    <table>
      <tr>
        <td colspan="3"> <h1>{{num1}}</h1></td>
      </tr>
      <tr>
        <td colspan="3"><h3>{{discount}}</h3></td>
      </tr>
      <tr>
        <td colspan="3"><h2>{{result}}</h2></td>
      </tr>
    </table>
    <table>
      <tr>
        <td colspan="3"><hr></td>
      </tr>
      <tr>
        <td><button @click="summation(0.9,'-10%')">10%</button></td>
        <td><button @click="summation(0.8,'-20%')">20%</button></td>
        <td><button @click="summation(0.7,'-30%')">30%</button></td>
      </tr>
      <tr>
        <td><button @click="summation(0.6,'-40%')">40%</button></td>
        <td><button @click="summation(0.5,'-50%')">50%</button></td>
        <td><button @click="summation(0.4,'-60%')">60%</button></td>
      </tr>
      <tr>
        <td colspan="3"><hr></td>
      </tr>
    </table>

    <table>
      <tr>
        <td><button @click="clickNum('7')">7</button></td>
        <td><button @click="clickNum('8')">8</button></td>
        <td><button @click="clickNum('9')">9</button></td>

      </tr>
      <tr>
        <td><button @click="clickNum('4')">4</button></td>
        <td><button @click="clickNum('5')">5</button></td>
        <td><button @click="clickNum('6')">6</button></td>

      </tr>
      <tr>
        <td><button @click="clickNum('1')">1</button></td>
        <td><button @click="clickNum('2')">2</button></td>
        <td><button @click="clickNum('3')">3</button></td>
      </tr>
      <tr>
        <td><button @click="clear()">c</button></td>
        <button @click="clickNum('0')">0</button>
        <td><button @click="backSpace()"><</button></td>

      </tr>
    </table>
  </div>
</template>
<script>
export default {
  name: 'hello',
  data () {
    return {
      result: '',
      num: '',
      num1: '',
      backNum: 0,
      discount: ''
    }
  },
  methods: {
    clickNum: function (num) {
      this.num1 += num
    },
    clear: function () {
      this.num1 = ''
      this.discount = ''
      this.result = ''
    },
    summation: function (dis, discountN) {
      this.result = this.num1 * dis
      this.discount = discountN
    },
    backSpace: function () {
      this.num1 = this.num1.substring(0, this.num1.length - 1)
    }
  }

}
</script>

<style >
table {
  margin: auto;
}



button {
    background-color: green; /* Green */
    border: none;
    width:100%;
    color: white;
    padding: 20px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 20px;
    font-family: 'Microsoft JhengHei UI';
    cursor: pointer;
}
</style>
