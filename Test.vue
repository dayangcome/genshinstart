<template>
    <div class="container">
        <el-button class="mybtn" @click="start">原神启动</el-button>
        <div class="overlay" ref="overlay"></div>
        <img class="image" ref="myimage" src="./yuanshen.svg">
    </div>
</template>

<script>
  export default{
    name:'Start',
    methods:{
        start(){
            const overlay = this.$refs.overlay;
            const myimage = this.$refs.myimage;
            overlay.style.visibility = 'visible';
            myimage.style.visibility = 'visible';
            overlay.style.opacity = 1 // 白色背景渐显
            
            setTimeout(() => {      //这里有一个回调地狱，期待大佬能够改进一下
                myimage.style.opacity = 1;
                setTimeout(() => {
                overlay.style.opacity = 0 
                myimage.style.opacity = 0;    //图片和白色背景一起渐隐
                setTimeout(() => {
                    this.fadeOut = false;
                    overlay.style.visibility = 'hidden';
                    myimage.style.visibility = 'hidden';
                }, 2000); // 2000毫秒后执行
                }, 5000); // 5000毫秒后执行
            }, 3500); // 3500毫秒后执行
        }
    }
  }
</script>

<style scoped>
.container{
    background-color: aqua;
    height: 680px;
}
.overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: white;
    opacity: 0;
    z-index: 1;
    visibility: hidden;
    transition: opacity 3s ease-in-out;
}
.image {
    width: 420px;
    position: fixed;
    top: 22%;
    left: 36%;
    z-index: 2;
    visibility: hidden;
    opacity: 0;
    transition: transform 2s ease-in-out, opacity 2s ease-in-out; 
}
.mybtn{  
    font-size: 18px;
    cursor: pointer;
    position: absolute;
    top: 40%; 
    left: 50%; 
    transform: translate(-50%, -50%); 
}
</style>
