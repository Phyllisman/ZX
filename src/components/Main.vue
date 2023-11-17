<template>
  <el-table :data="tableData">
    <el-table-column prop="id" label="ID" width="120">
    </el-table-column>
    <el-table-column prop="username" label="用户名" width="120">
    </el-table-column>
    <el-table-column prop="email" label="邮箱" width="120">
    </el-table-column>
    <el-table-column prop="phone" label="电话">
    </el-table-column>

  </el-table>
</template>

<script>
export default {
  name: 'Main',
  components: {
  },
  data() {

    return {
      tableData: []
    }
  },
  methods:{
    loadGet(){
      this.$axios.get('http://www.xiaolin.fun:8080/user/all').then(res=>res.data).then(res=>{
        console.log(res.data)
        this.tableData=res.data
      })
    },
    loadPost(){
      this.$axios.post('http://www.xiaolin.fun:8080/user/all').then(res=>res.data).then(res=>{
        console.log(res)
        //this.tableData=res
      })
    }
  },

  beforeMount() {
    this.loadGet()
    //this.loadPost()
  }
}
</script>

<style>
</style>
