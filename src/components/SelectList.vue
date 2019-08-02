<template>
  <div class='app-holder'> 
    <div class="listHolder">
     <h3 class="title">Quantity</h3>
     <select @change="handleChange" class='selectInput'>
        <option v-for='option in selectList' :key="option">{{option === 10 ? option + '+' : option}}</option>
      </select>
    </div>
      <QuantityInput v-if='initValue === 10' @add-value='addNewNum'/>
  </div>
</template>

<script>

import QuantityInput from './QuantityInput'

export default {
  name: 'SelectList',
  components: {
    QuantityInput
  },

  data() {
    return {
      selectList : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
      initValue: 0
    }
  },

  methods: {
    handleChange(e){
      this.initValue = parseInt(e.target.value);
    },
    addNewNum(value){
      if(!value && value !== 0){
          alert('Please enter a number')
          return false         
        }
      else if(this.selectList.includes(value)){
            alert('That number already exists');
            return false
        }
      else{
          this.selectList = [...this.selectList, value].sort((a,b) => a-b)
        }
        return true
    }
  }
}
</script>

<style scoped>
  .app-holder{
    display: flex;
  }
  .title{
    color: #666666;
  }
  .listHolder{
    width: 150px;
    border:1px solid #666;
    padding-bottom: 15px;
    text-align: center;
}
.selectInput{
    max-width: 70%;
}
</style>



