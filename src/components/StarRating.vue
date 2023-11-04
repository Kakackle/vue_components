<script setup>
import { ref } from 'vue';
const hover_val = ref(0);
const chosen_val = ref(0);

import { defineProps } from 'vue';
const props = defineProps({
    stars: {
        default: 5,
    },
})

const star_amount = props.stars;

const is_filled = (index) => {
    let display = 0;
    display = hover_val.value > 0 ? hover_val.value : chosen_val.value;
    // console.log(`display>=: ${display>=index}`);
    if (display >= index) return true
    else return false
}

</script>

<template>
<div class="container" @mouseleave="hover_val = 0">
    <div class="star-div" v-for="i in star_amount"
    :key="i"
    @click="chosen_val = i"
    @mouseenter="hover_val = i">
        <ion-icon name="star" v-if="is_filled(i)" class="star"></ion-icon>
        <ion-icon name="star-outline" v-else class="star"></ion-icon>
    </div>
    <!-- <ion-icon :name="'star' + is_filled(i) ? '' : '-outline'" class="star" -->
    <!-- ></ion-icon> -->
</div>
<p>hover_val: {{ hover_val }}</p>
<p>chosen_val: {{ chosen_val }}</p>
</template>

<style scoped>
.container{
    display: flex;
    align-items: center;
    border: 2px solid var(--gray);
}

.star{
    width: 40px;
    height: 40px;
    padding: 5px;
    visibility: visible;
}

.star:hover{
    cursor: pointer;
}
</style>