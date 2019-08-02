<template>
    <div class='quantityHolder'>
        <h3 class="title">Quantity</h3>
       <form @submit="onSubmit" class='formHolder'>
           <input type="number"  @change="handleChange" :value='value' class="inputHolder"/>
           <input type="submit" class="submit-btn"/>
       </form>
    </div>
</template>

<script>
export default {
    name: 'QuantityInput',
    methods: {
        onSubmit(e) {
            e.preventDefault()
            if(this.value < 0){
                alert('Number must be greater than 0');
                this.value = null
            }
            else{
                this.$emit('add-value', parseInt(this.value));
                this.value = null
            }
        },

        handleChange(e) {
            this.value = e.target.value;
        }
    },

    data() {
        return {
            value: null
        }
    }
}
</script>

<style scoped>
    .quantityHolder{
        width:150px;
        border:1px solid #666;
        padding-bottom:15px;
        margin-left: 50px
    }
    .title{
        color:#666666;
        text-align:center
    }

    .formHolder{
        max-width: 70%;
        margin-left: 10px;
    }
    .inputHolder{
        max-width:80px;
        margin-bottom:3px
    }

    .submit-btn{
        width: 80px;
    }
</style>
