<template>
<div class="imageUploadCard">
  <div style="font-size: 20px;margin-bottom: 10px">⭐当前模板：{{modelid.name}}</div>
  <el-upload
    class="upload-demo"
    ref="upload"
    action=""
    :multiple="false"
    :http-request="handleUpload"
    :show-file-list="false"
    :on-change="handleChange"
    :on-remove="handleRemove"
    :before-upload="beforeUpload"
    :file-list="fileList"
    :auto-upload="false">
    <!--          <el-button slot="trigger" size="small" type="primary">++</el-button>-->
    <el-image slot="trigger"  id="img-preview" :src="imgStream">
      <el-button slot="error">选择图片</el-button>
    </el-image>
  </el-upload>
  <el-button v-show="imgStream!==''">测试</el-button>
</div>
</template>

<script>
export default {
  name: "function1test",
  props: ['modelid'],
  data() {
    return {
      fileList: [],
      imgStream: ''
    }
  },
  methods:{
    resetImg(){
      this.fileList=[];
      this.imgStream=''
    },
    submitUpload () {
      this.$refs.upload.submit();
    },
    setImgUrl(raw){
      this.imgStream=window.URL.createObjectURL(raw)
    },
    handleRemove (file, fileList) {
      // console.log(file, fileList);
      this.fileList=fileList;
    },
    handleChange(file,fileList){
      if (fileList.length>0) {
        this.fileList=[fileList[fileList.length-1]]
      }
      // this.fileList=fileList
      this.setImgUrl(file.raw)
    },
    // handleExceed(file,fileList){
    //   this.fileList=[file[0]]
    //   this.setImgUrl(file[0])
    // },
    beforeUpload(file){
      const isJPG = file.type === 'image/jpeg' || file.type === 'image/png';
      const isLt2M = file.size / 1024 / 1024 < 20;
      if (!isJPG) {
        this.$message.error('上传头像图片只能是 JPG 格式!');
      }
      if (!isLt2M) {
        this.$message.error('上传头像图片大小不能超过 20MB!');
      }
      return isJPG && isLt2M;
    },
    handleUpload(){

    }
  }
}
</script>

<style scoped>
#img-preview{
  width: 100%;
  height: 100%;
}
.imageUploadCard{
  text-align: center;
  /*min-height: 300px;*/
  /*line-height: 300px;*/
}
.imageUploadCard /deep/ .upload-demo{
  width: 100%;
  height: 100%;
  /*line-height: 300px;*/
}
.imageUploadCard /deep/ .el-image__error{
  width: 100%;
  height: 100%;
  /*line-height: 300px;*/
}
.imageUploadCard /deep/ .el-upload--text{
  width: 100%;
  /*height: 100%;*/
}
.el-image{
  width: 100%;
  height: 100%;
  border-radius: 15px;
  border:dashed 3px;

}
.el-image .el-button{
  width: 100%;
  height: 100%;
  border-radius: 15px;
  font-size: 20px;
}
</style>
