<template>
  <div class="details container">
  	<router-link to="/" class="layui-btn layui-btn-sm"><i class="layui-icon"></i>&nbsp;返回</router-link>
    <h1 class="page-header">
    	{{customer.name}}

    	<span class="pull-right">
    		<router-link class="btn btn-primary" v-bind:to="'/edit/'+customer.id">
    		<i class="layui-icon"></i>	&nbsp;编辑
    		</router-link>
    		<button class="btn btn-danger" v-on:click="deleteCustomer(customer.id)">
        <i class="layui-icon"></i>&nbsp;删除</button>
    	</span>
    </h1>
    <ul class="list-group">
    	<li class="list-group-item">
    		<span class="glyphicon glyphicon-asterisk">
    			{{customer.myid}}
    		</span>
    	</li>
    	<li class="list-group-item">
    		<span class="layui-icon layui-icon-username">
    			{{customer.name}}
    		</span>
    	</li>
      <li class="list-group-item">
        <span class="layui-icon layui-icon-male ">

    			{{customer.sex}}
        </span>

    	</li>
      <li class="list-group-item">
    		<span class="layui-icon layui-icon-cellphone">
    			{{customer.phone}}
    		</span>
    	</li>
      <li class="list-group-item">
    		<span class="glyphicon glyphicon-paperclip">
    			{{customer.email}}
    		</span>
    	</li>



    	<li class="list-group-item">
    		<span class="layui-icon layui-icon-menu-fill">
    			{{customer.education}}
    		</span>
    	</li>
    	<li class="list-group-item">
    		<span class="layui-icon layui-icon-release">
    			{{customer.graduationschool}}
    		</span>
    	</li>

		<li class="list-group-item">
			<span class="layui-icon layui-icon-fonts-code">
				{{customer.profession}}
			</span>
		</li>
    <li class="list-group-item">
      <span class="glyphicon glyphicon-usd">
				{{customer.salary}}
      </span>
		</li>
    <li class="list-group-item">
			<span class="glyphicon glyphicon-home">
				{{customer.address}}
			</span>
		</li>
    <li class="list-group-item">
			<span class="layui-icon layui-icon-date">
				{{customer.data}}
			</span>
		</li>
    <li class="list-group-item">
			<span class="glyphicon glyphicon-credit-card">
				{{customer.card}}
			</span>
		</li>
    <li class="list-group-item">
			<span class="glyphicon glyphicon-comment">
				{{customer.profile}}
			</span>
		</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'cumstomerdetails',
  data () {
    return {
      customer:""
    }
  },
  methods:{
  	fetchCustomers(id){
      this.$http.get("http://localhost:3000/users/"+id)
          .then(function(response){
            // console.log(response);
            this.customer = response.body;
          })
    },
    deleteCustomer(id){
    	// console.log(id);
        if(confirm("确定删除该联系人信息吗？")){
          this.$http.delete("http://localhost:3000/users/"+id)
        		.then(function(response){

                    layui.use('layer', function(){
                          var layer = layui.layer;
                          layer.msg('删除用户成功!');
                    });

        			this.$router.push({path:"/"});
                })
          }
    }
  },
  created(){
  	this.fetchCustomers(this.$route.params.id);
  }
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
