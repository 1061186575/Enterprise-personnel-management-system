<template>
  <div class="customers container">
    <h1 class="page-header">企业人事管理系统</h1>
    <!-- <i class="layui-icon layui-icon-search"></i> -->
    <input type="text" class="form-control " placeholder="姓名搜索" v-model="filterInput">


    <br>
    <table class="table table-striped">
      <thead>
        <tr>
          <th id="myid">ID</th>
          <th id="name">姓名</th>
          <th id="sex">性别</th>
          <th id="profession">职务</th>
          <th id="phone">电话</th>
          <th id="email">邮箱</th>

        </tr>
      </thead>

      <tbody>
        <tr v-for="customer in filterBy(customers,filterInput)" :key="customer.id">
          <td>{{customer.myid}}</td>
          <td>{{customer.name}}</td>
          <td>{{customer.sex}}</td>
          <td>{{customer.profession}}</td>
          <td>{{customer.phone}}</td>
          <td>{{customer.email}}</td>
          <td><router-link class="layui-btn layui-btn-sm layui-btn-normal" v-bind:to="'/customer/'+customer.id">详情</router-link></td>
        </tr>
      </tbody>

    </table>
  </div>
</template>

<script>

export default {
  name: 'customers',
  data () {
    return {
      customers:[],
      filterInput:""
    }
  },
  methods:{
    fetchCustomers(){
      this.$http.get("http://localhost:3000/users")
          .then(function(response){
            console.log(response);
            this.customers = response.body;
          })
    },
    filterBy(customers,value){
      return customers.filter(function(customer){
         return customer.name.match(value);
      })
    }
  },
  created(){
    this.fetchCustomers();
  },
  components:{

  }
}
</script>

<style scoped>

    #myid{
        width: 120px;
    }
    #name{
        width: 120px;
    }
    #sex{
        width: 100px;
    }
    #profession{
        width: 150px;
    }
    #phone{
        width: 150px;
    }
    #email{
        width: 260px;
    }
</style>
