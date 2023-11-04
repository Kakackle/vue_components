<script setup>
import { defineProps, ref } from 'vue';
const props = defineProps({
    width: {
        type: Number,
        default: 200
    },
    items: {
        type: Array,
        required: true
    },
});

const isOpen = ref(false);

</script>

<template>
<div class="container" :style="{width: props.width + 'px'}">
    <!--<ion-icon name="chevron-down-outline"></ion-icon>-->
    <div class="top">
        <p class="text-basic text-center">MENU</p>
        <ion-icon :name="isOpen? 'menu': 'chevron-down' + '-sharp'" class="icon-basic icon-menu"
        @click="isOpen = !isOpen"></ion-icon>
    </div>
    <!-- <p>{{ isOpen }}</p> -->
    <Transition name="slide">
    <ul class="dropdown-list" v-if="isOpen">
        <li class="item" v-for="(item, index) in props.items"
        :class="{odd: index%2==1 }">{{ item }}</li>
    </ul>
    </Transition>
</div>
</template>

<style scoped>
.container{
    /* border: 2px solid var(--gray); */
    border-radius: 3px;
    /* height: 40px; */
    /* width: 200; */
    position: relative;
    /* border: 2px solid var(--gray-light); */
}
.top{
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 36px;
    border: 2px solid var(--gray);
}

.text-center{
    width: 100%;
    justify-self: center;
}

.icon-menu{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 24px;
    width: 24px;
    padding: 4px;
}

.icon-menu:hover{
    cursor: pointer;
    border: 2px solid var(--gray-dark);
    border-radius: 3px;
}

.dropdown-list{
    display: flex;
    flex-direction: column;
    width: 100%;
    gap: 0;
    border: 2px solid var(--gray-light);
    position: absolute;
    top: 34px;
    list-style: none;
    /* top: 40px; */
    /* transform: translateY(-50%); */
    /* padding: 0px 2px; */
    align-items: center;
    z-index: -1;
}

.item:hover{
    filter: brightness(0.75);
    cursor: pointer;
}

.odd{
    background-color: var(--gray-light);
}

.item{
    width: 100%;
    padding: 2px;
}

.slide-enter-active {
    transition: all 0.3s ease-in;
}

.slide-leave-active {
    transition: all 0.3s ease-out;
}

.slide-enter-from,
.slide-leave-to{
    opacity: 0;
    transform: translateY(-10px);
}
</style>