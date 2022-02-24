<template>
    <div class="progress-bar">
      <span class="absolute">{{progress}}%</span> 
      <div 
      class="bar" 
      :style="{ width: progress + '%' }" >
      </div>
    </div>
</template>

<script>
export default {
  props:{
    progress : { type: Number, required: true}
  }

}
</script>

<style scoped>


.progress-bar{
  width: 90%;
  height: 40px;
  border: 2px solid black;
  margin: 20px auto ; 
  text-align: center;
}

.bar{
  background-color: rgb(60, 255, 0);
  height: 40px;
  font-size: 25px;
}

.absolute{
  position: absolute;
}


</style>