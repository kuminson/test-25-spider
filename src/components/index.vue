<template>
  <section class="index">
    <div class="search">
      <!--卡片-->
      <el-card class="box-card">
        <div slot="header" class="form">
          <span>搜索条件</span>
        </div>
        <div class="formbox">
          <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
            <el-form-item label="职位" prop="pos">
              <el-input v-model="ruleForm.pos"></el-input>
            </el-form-item>
            <el-form-item label="公司" prop="com">
              <el-input v-model="ruleForm.com"></el-input>
            </el-form-item>
            <el-form-item label="地点" prop="add">
              <el-input v-model="ruleForm.add"></el-input>
            </el-form-item>
            <el-form-item label="薪水" prop="sal">
              <el-input v-model="ruleForm.sal"></el-input>
            </el-form-item>
            <el-form-item label="时间" prop="time">
              <el-date-picker v-model="ruleForm.time" type="date" placeholder="选择日期" class="timebox"></el-date-picker>
            </el-form-item>
            <el-form-item label-width="0">
              <el-button @click="resetForm('ruleForm')">重置</el-button>
              <el-button type="primary" @click="submitForm('ruleForm')">搜索</el-button>
            </el-form-item>
          </el-form>
        </div>
      </el-card>
    </div>
    <div class="table">
      <el-card class="box-card">
        <div slot="header" class="form">
          <span>搜索内容</span>
        </div>
        <div class="tablebox">
          <el-table :data="tableData" stripe style="width: 100%" border height="500">
            <el-table-column prop="pos" label="职位" width="180"></el-table-column>
            <el-table-column prop="com" label="公司" ></el-table-column>
            <el-table-column prop="add" label="地点" ></el-table-column>
            <el-table-column prop="sal" label="薪水" width="180"></el-table-column>
            <el-table-column prop="time" label="时间" width="180"></el-table-column>
          </el-table>
        </div>
      </el-card>
    </div>
  </section>
</template>

<script>
  export default {
    name: "index",
    data () {
      return {
        ruleForm: {
          pos: '',
          com: '',
          add: '',
          sal: '',
          time: ''
        },
        rules: {
          pos: [
            { required: true, message: '请输入职位', trigger: 'change' }
          ],
          com: [
          ],
          add: [
            { required: true, message: '请输入地点', trigger: 'change' }
          ],
          sal: [
          ],
          time: [
          ]
        },
        tableData: [{
          pos: '职位',
          com: '公司',
          add: '地点',
          sal: '薪水',
          time: '时间'
        }, {
          pos: '职位',
          com: '公司',
          add: '地点',
          sal: '薪水',
          time: '时间'
        }, {
          pos: '职位',
          com: '公司',
          add: '地点',
          sal: '薪水',
          time: '时间'
        }, {
          pos: '职位',
          com: '公司',
          add: '地点',
          sal: '薪水',
          time: '时间'
        }]
      }
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>

<style scoped>
  .search{
    width: 600px;
    margin-left: auto;
    margin-right: auto;
  }
  .timebox{
    width: 100%;
  }
  .table{
    margin-top: 30px;
    width: 1000px;
    margin-left: auto;
    margin-right: auto;
  }
  .tablebox{
    text-align: left;
  }
</style>
