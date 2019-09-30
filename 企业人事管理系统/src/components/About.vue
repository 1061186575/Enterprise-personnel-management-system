<template>
<div class="global">
  <div class="right">
    <h1> 我们公司是******公司，...，欢迎加入我们！</h1>
    <h1>   地址：湖南省**市*******</h1>
  </div>

  <div class="left">

    <h1 class="">联系我们：</h1>
    <h1>手机号：***</h1>
    <h1>微信号：wx****</h1>

  </div>
</div>
</template>

<script>
export default {
  name: 'about',
  data() {
    return {

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.global {
  margin: 10px auto;
  width: 1000px;
  height: 1000px;
  /* border: 2px solid red; */
}

.left {
  margin-top: 100px;
  width: 1000px;
  height: 100px;
  text-align: center;
  background-color: rgb(29, 89, 191);
  position: relative;
  /* 其他浏览器 */
  animation: mymove-left 12s infinite;
  /* Safari and Chrome */
  -webkit-animation: mymove-left 12s infinite;
  padding: 120px;
}

.left:hover {
  border: 10px solid #000;
  color: #fff;
}

.right:hover {
  border: 10px solid #000;
  color: #fff;
}

.right {
  background-color: rgb(221, 20, 20);
  width: 1000px;
  height: 400px;
  padding: 120px;

  text-align: center;
  position: relative;

  animation: mymove-right 12s infinite;
  -webkit-animation: mymove-right 12s infinite;

}

@-webkit-keyframes mymove-left {
  0% {
    top: 0px;
    left: 0px;
    background: blue;
    height: 570px;
  }
  16.6% {
    top: -10px;
    left: 10px;
    background: purple;
    height: 550px;
  }
  33.5% {
    top: -10px;
    left: 20px;
    background: red;
    height: 570px;
  }
  50% {
    top: 0px;
    left: 30px;
    background: rgb(221, 236, 51);
    height: 590px;
  }
  66.5% {
    top: 10px;
    left: 20px;
    background: orange;
    height: 570px;
  }
  83.2% {
    top: 10px;
    left: 10px;
    background: green;
    height: 550px;
  }
  100% {
    top: 0px;
    left: 0px;
    background: purple;
    height: 570px;
  }
}

@-webkit-keyframes mymove-right {
  0% {
    top: 0px;
    right: 0px;
    background: red;
  }
  16.6% {
    top: -10px;
    right: 10px;
    background: rgb(221, 236, 51);
  }
  35.5% {
    top: -10px;
    right: 20px;
    background: orange;
  }
  50% {
    top: 0px;
    right: 30px;
    background: green;
  }
  66.5% {
    top: 10px;
    right: 20px;
    background: blue;
  }

  83.2% {
    top: 10px;
    right: 10px;
    background: purple;
  }
  100% {
    top: 0px;
    right: 0px;
    background: blue;
  }
}


</style>
