<template>
    <div class="discount">
        <h4>지금 결제하면 {{discountData}}% 할일</h4>
    </div>


</template>

<script>
export default {
    name : 'Discount',

    data(){
        return{
            discountData : 30
        }
    },

    //Life cycle hook 사용법
    mounted(){
        var interval = setInterval(() => {
            this.discountData--;
            if(this.discountData == 0 ){
                clearInterval(interval);
            }
        }, 1000)


    }
}
</script>

<style>
    
</style>