<template>
<!-- modal -->
    <div class="black-bg" v-if="modalOpen == true">
        <div class="white-bg"> 
            <img :src="roomInfo[click].image" class="room-img">
            <h4>{{roomInfo[click].title}}</h4>
            <p>{{roomInfo[click].content}}</p>
            <!-- $event == JS evnetListener와 같음 -->
            <!-- <input @input="month = $event.target.value"> -->

            <input v-model.number="month">
            <p> {{month}}개월 선택함 : {{roomInfo[click].price * month}}원</p>
            <button @click="modalCloseSend">닫기</button>
            <!-- props는 read-only임... 수정하면 안됨 -->
        </div>
    </div>
</template>

<script>
export default {
    name: 'Modal',
    data(){
        return {
            month : 1,
        }
    },
    //감시 역할 month가 변할 때마다 여기 있는 month()실행
    watch : {
        
    },

    props : {
        roomInfo : Object, // 왼쪽은 받은 데이터명, 오른쪽은 데이터 타입
        click : Number,
        modalOpen : Boolean,
    },
    methods: {
        modalCloseSend(){
            this.$emit('openModal')
        }
    },
    updated(){
        if(this.month == 2){
            alert("3개월부터 계약 가능합니다 ㅜㅜ");
        }
    }
}
</script>

<style>

</style>