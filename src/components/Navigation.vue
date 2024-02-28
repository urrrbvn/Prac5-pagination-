<script setup>
import { computed, defineProps, onMounted, reactive, ref } from 'vue';

const props = defineProps({
    createSlice: Function
})

const buttons = 5

const currentPage = ref(1)


function handler(id){
    if(props.createSlice){
        props.createSlice(currentPage.value, id)
        currentPage.value = id
        console.log(currentPage.value)
    }else{
        console.log('Ошибка!')
    }
}

onMounted(()=>{
    console.log(currentPage.value)
    props.createSlice(currentPage.value, 1)
})

function nextPage(id){
    if((id+1)!== 6){
        const nextBtn = document.getElementById(id+1)
        nextBtn.click()
    }else{
        return
    }
}

function prevPage(id){
    if((id-1)!== 0){
        const prevtBtn = document.getElementById(id-1)
        prevtBtn.click()
    }else{
        return
    }
}

</script>

<template>
    <div class="navCont">
        <button id="pageBack" @click="prevPage(currentPage)" >&lt;</button>
        <div class="pages">
            <button v-for="elem in Array.from({length: buttons}, (_, elem) => elem + 1)" 
                                                                            :id = "elem"
                                                                            :key="elem"
                                                                            :previous="elem-1"
                                                                            @click="handler(elem)"
                                                                            :style="{backgroundColor: elem == currentPage ? '#185BC3' : 'white'}"
                                                                            >
                {{ elem }}
            </button>
        </div>
        <button id="nextPage" @click="nextPage(currentPage)">&gt;</button>
    </div>
</template>

<style>
    .navCont{
        display: flex;
        flex-direction: row;

        width: 558px;
        height: 84px;

        padding: 10px;

        gap: 20px;

    }
    .pages{
        display: flex;
        flex-direction: row;
        gap: 20px;
    }
    button{
        width: 64px;
        height: 64px;
        border-radius: 6px;
        border: 1px solid #BDBDBD;
        background-color: white;

        display: flex;
        align-items: center;
        justify-content: center;

        font-size: 18px;
        font-weight: 800;

        color: #BDBDBD;
    }
</style>