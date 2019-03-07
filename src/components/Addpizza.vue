<template>
  <div>
    <div class="form-group">
      <h3 class="text-warning text-center" >添加新pizza</h3>
      <label for="exampleInputEmail1">品种</label>
      <input type="text" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="给这个pizza添加个名字吧" v-model="newitem.title">
    </div>
    <div class="form-group">
      <label for="exampleInputEmail1">商品描述</label>
     <textarea cols="40" rows="2" placeholder="请输入商品相应的描述" v-model="newitem.des"></textarea>
    </div>
    <h4>尺寸&价格</h4>
    <div class="box1">
    尺寸：
    <select v-model="newitem.size1">
      <option>5</option>
      <option>7</option>
      <option selected>9</option>
      <option>14</option>
    </select>
    价格：
    <input type="text" class="form-control ipt" v-model="newitem.price1">
  </div>
    <div class="box2 mt-4">
      尺寸：
      <select v-model="newitem.size2">
        <option>5</option>
        <option selected>7</option>
        <option>9</option>
        <option>14</option>
      </select>
      价格：
      <input type="text" class="form-control ipt"  v-model="newitem.price2">
    </div>


    <button type="submit" class="btn btn-primary mt-4 btn-block" @click.parevent="addnew">添加新的pizza</button>
  </div>
</template>

<script>
  import axios from 'axios'
    export default {
        name: "Addpizza",
        data () {
          return {
            newitem:{},

          }
        },
      methods:{
        addnew(){
          var data ={
            title:this.newitem.title,
            text:this.newitem.des,
            sitem:[
              {
                size:this.newitem.size1,
                price:this.newitem.price1,
              },
              {
                size:this.newitem.size2,
                price:this.newitem.price2,
              }
            ]
          };
          axios.post('./menu-cc.json',data)
            .then((res)=>{
              console.log(res.data)
            })
        }
      }
    }
</script>

<style scoped>
.ipt{
  display: inline-block;
  width: 150px;
}

</style>
