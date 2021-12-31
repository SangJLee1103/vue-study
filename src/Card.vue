<template>
    <div>
        <img :src="roomInfo.image" class="room-img">
        <h4 @click="openModalSend">{{roomInfo.title}}</h4>
        <p>{{roomInfo.price}}원</p>
        <!-- v-on과 @는 같음 -->
    </div>
</template>

<script>
export default {
    name : 'Card',
    props : {
        roomInfo : Object,
    },
    methods: {
        openModalSend(){
            this.$emit('openModal', this.roomInfo.id)
        }
    },
}
</script>

<style>

</style>