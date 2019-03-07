<template>
  <div class="menu container row">
    <div class="box1 col-8 ml-6">
      <h3 class="text-primary text-center">点餐</h3>
      <table class="table" v-for="(item1,index1) in item" :key="index1">
        <thead class="bg-primary">
        <tr>
          <th scope="col" class="text-center">尺寸</th>
          <th scope="col" class="text-center">价格（元）</th>
          <th scope="col" class="text-center">加入</th>
        </tr>
        </thead>
        <tbody>
        <tr>
          <th scope="row" class="text-center" colspan="3"><h2>{{item1.title}}</h2></th>
        </tr>
        <tr>
          <th scope="row" class="text-center" colspan="3"><h5>{{item1.text}}</h5></th>
        <tr v-for="(item2,index2) in item1.sitem" :key="index2">
          <th scope="row" class="text-center">{{item2.size}}</th>
          <td class="text-center">{{item2.price}}</td>
          <td class="text-center" @click="addData(item1,item2)"><button>+</button></td>
        </tr>
        </tbody>
      </table>
    </div>
    <div id="box" col-4>
      <h3 class="text-primary text-center">购物车</h3>
      <table class="table">
        <thead class="bg-primary">
        <tr>
          <th scope="col" class="text-center">数量</th>
          <th scope="col" class="text-center">种类</th>
          <th scope="col" class="text-center">价格</th>
        </tr>
        </thead>
        <tbody>
          <template v-if="newitem.length>0">
            <tr v-for="(newitem1,index2) in newitem" :key="index2">
              <th scope="row" class="text-center">
                <button @click="reduce(newitem1,index2)">-</button>
                <input type="number" v-model.number="newitem1.quantity" class="ipt1">
                <button @click="add(newitem1)">+</button>
              </th>
              <td class="text-center">{{newitem1.name}}--{{newitem1.size}}</td>
              <td class="text-center">{{newitem1.price*newitem1.quantity}}</td>
              <tr>总件数：{{newitem.length}}</tr>
              <tr>总价：{{tatol}}</tr>
            </tr>
          </template>
          <template v-else>
            <tr>
              <td colspan="3">此购物车空空如也！</td>
            </tr>
          </template>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    name: 'Menu',
    data () {
      return {
        newitem:[],
        item:{}
        // item:[{
        //   title:'榴莲pizza',
        //   text:'这是大众喜爱的pizza',
        //   sitem:[
        //     {
        //       size:'七寸',
        //       price:'70',
        //     },
        //     {
        //       size:'10寸',
        //       price:'100',
        //     }
        //   ]
        // },
        //   {
        //     title:'西瓜pizza',
        //     text:'这是独特的pizza',
        //     sitem:[
        //       {
        //         size:'七寸',
        //         price:'50',
        //       },
        //       {
        //         size:'10寸',
        //         price:'80',
        //       }
        //     ]
        //   }
        // ]
      }
    },
    //加载获取
    mounted(){
      axios.get('./menu-cc.json')
        .then(res=>{
          this.item=res.data
        })
    },
    computed:{
      tatol(){
        return this.newitem.reduce((pre,cur)=>{
          return pre+cur.quantity*cur.price
        },0)
      }
    },
    methods:{
      addData(item1,item2){
        //点击添加时，实现去重
        //当前展示的这一项与我们输出的吻合时，quantity+1
        var result=this.newitem.filter((item3)=>{
          return item1.title==item3.name&&item2.size==item3.size
        })

        if (result!=null&&result.length>0){
          if (result[0].quantity>=10){
            result[0].quantity=10
          }else {
            result[0].quantity++
          }

        } else{
          this.newitem.push({
            name:item1.title,
            size:item2.size,
            quantity:1,
            price:item2.price
          })
        }

      },
      reduce(newitem1,index2){
        if (newitem1.quantity<=1){
          this.newitem.splice(index2,1)
        } else {
          newitem1.quantity--
        }

      },
      add(newitem1){
        if (newitem1.quantity>=10){
          newitem1.quantity=10
        }else {
          newitem1.quantity++
        }

      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.ipt1{
  width: 50px;
}

</style>
