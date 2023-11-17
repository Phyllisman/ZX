<template>
  <div>
    <div style="margin-bottom: 5px;">
      <el-input placeholder="请输入名字" suffix-icon="el-icon-search" style="width:200px;"></el-input>
      <el-button type="primary" style="margin-left: 5px;" @click="loadGet">查询</el-button>
      <el-button type="success">重置</el-button>
      <el-button type="primary" style="margin-left: 5px;" @click="add">新增</el-button>
    </div>
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
    <el-pagination
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page="pageNum"
        :page-sizes="[100, 200, 300, 400]"
        :page-size="100"
        layout="total, sizes, prev, pager, next, jumper"
        :total="total">
    </el-pagination>
    <el-dialog
        title="提示"
        :visible.sync="centerDialogVisible"
        width="30%"
        center>
        <el-form ref="form"  label-width="80px" size="mini">
          <el-form-item label="用户名">
            <el-input></el-input>
          </el-form-item>
          <el-form-item label="邮箱">
            <el-input></el-input>
          </el-form-item>
          <el-form-item label="电话">
            <el-input></el-input>
          </el-form-item>
        </el-form>
        <span slot="footer" class="dialog-footer">
          <el-button @click="centerDialogVisible = false">取 消</el-button>
          <el-button type="primary" @click="centerDialogVisible = false">确 定</el-button>
        </span>
    </el-dialog>
  </div>
</template>

<script>
export default {
  name: 'Main',
  components: {
  },
  data() {

    return {
      tableData: [],
      pageNum:10,
      total:1,
      centerDialogVisible:false
    }
  },
  methods:{
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`);
    },
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
    },
    add(){
      this.centerDialogVisible=true
    },
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
