<template>
<!-- modal -->
    <div class="black-bg" v-if="modalOpen == true">
        <div class="white-bg"> 
            <img :src="roomInfo[click].image" class="room-img">
            <h4>{{roomInfo[click].title}}</h4>
            <p>{{roomInfo[click].content}}</p>
            <p>{{roomInfo[click].price}}원</p>
            <!-- <button @click="modalOpen = false">닫기</button> -->
        </div>
    </div>
</template>

<script>
export default {
    name: 'Modal',
    props : {
        roomInfo : Object, // 왼쪽은 받은 데이터명, 오른쪽은 데이터 타입
        click : Number,
        modalOpen : Boolean,
    }
}
</script>

<style>

</style>