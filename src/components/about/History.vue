<template>
  <div class="history row">
    <div class="card col-4" v-for="(item,index) in items" :key="index">
      <img class="card-img-top" :src="item.imgsrc" alt="Card image cap" >
      <div class="card-body">
        <h5 class="card-title">{{item.title}}</h5>
        <p class="card-text">{{item.text}}</p>
      </div>
    </div>
  </div>
</template>

<script>
  //1.通过import引入图片路径
  //2.通过require引入图片路径
  //3.图片直接存储于static文件夹里
  // import sf from '../../assets/pizza1.jpg'
  // import yt from '../../assets/pizza2.jpg'
  // import zt from '../../assets/pizza3.jpg'

  export default {
    name: 'History',
    data () {
      return {
        items:[
          {title:'大米',text:'大米好吃',imgsrc:require('../../assets/pizza1.jpg')},
          {title:'小米',text:'小米好吃',imgsrc:require('../../assets/pizza2.jpg')},
          {title:'玉米',text:'玉米好吃',imgsrc:require('../../assets/pizza3.jpg')}
        ]
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


</style>
