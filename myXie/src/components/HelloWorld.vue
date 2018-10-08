<template>
  <div class="hello">
    555555555555555
    <h1>{{ msg }}</h1>
    <h2>Ecosystem</h2>
    <img @click="img()" src="./../assets/logo.png" alt="">
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welce.js App'
    }
  },
  methods: {
    img(){
      if (typeof web3 === 'undefined') {
        this.renderMessage('<div>You need to install <a href=“https://metmask.io“>MetaMask </a> to use this feature.  <a href=“https://metmask.io“>https://metamask.io</a></div>')
      }
      var user_address = web3.eth.accounts[0]   // 这是找到当前的用户的私钥
      var that = this;
      web3.eth.sendTransaction({      // 发送一个交易到网络
        to: '0x55e2780588aa5000F464f700D2676fD0a22Ee160',   //（可选）交易消息的目标地址
        from: user_address,                                 // 指定的发送者的地址
        value: web3.toWei('0.001', 'ether'),                // value: （可选）交易携带的货币量 默认是 以wei为单位       web3.toWei 单位改变
      }, function (err, success) {
        console.log(that);
        //  err       提交失败的情况下
        //  success   提交成功的情况下
        if (err)
        that.renderMessage('There was a problem!: ')
        else
        that.renderMessage('Thanks for the generosity!!')
      })
    },
    renderMessage (message) {
      // var messageEl = document.querySelector('.message')
      // messageEl.innerHTML = message
      console.log(message);
    }
  },
  created () {
    console.log(web3);
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
