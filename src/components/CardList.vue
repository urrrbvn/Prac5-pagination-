<template>
    <div class="cardList">
            <CardItem v-for="elem in currentSlice"
            :name="elem.name"
            :difficulty="elem.difficulty"
            :cuisine="elem.cuisine"
            :calories="elem.caloriesPerServing"
            :ingredients="elem.ingredients"
            :img="elem.image"
            ></CardItem>
    </div>
</template>

<script setup>

    import CardItem from './CardItem.vue';
    
    const props = defineProps({
        currentSlice: Array
    })

</script>

<style>
    .cardList{
        display: grid;

        grid-template-columns: 224px 224px 224px;
        grid-auto-rows: 443px;

        gap: 75px;
        justify-content: center;
    }
</style>