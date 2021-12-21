<template>
    <div v-for="(room, i) in roomInfo" :key="i">
        <img :src="roomInfo[i].image" class="room-img">
        <h4>{{roomInfo[i].title}}</h4>
        <p>{{roomInfo[i].price}}원</p>
        <!-- v-on과 @는 같음 -->
    </div>
</template>

<script>
export default {
    name : 'Card',
    props : {
        roomInfo : Object,
        i : Number,
    }
}
</script>

<style>

</style>