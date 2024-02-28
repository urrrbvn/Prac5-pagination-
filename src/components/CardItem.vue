<template>
    <div class="card">
        <img :src="props.img" alt="" width="224" height="176.76">
        <h1>{{ props.name }}</h1>
        <div class="cardInfo">
            <p>Difficulty: {{ props.difficulty }}</p>
            <p>Cuisine: {{ props.cuisine }}</p>
            <p>Calories per Serving: {{ props.calories }}</p>
        </div>
        <div class="cardIngredients">
            ingredients:
            <ul>
                <li v-for="elem in props.ingredients">{{ elem }}</li>
            </ul>
        </div>
    </div>
</template>

<script setup>

const props = defineProps({
    name: String,
    difficulty: String,
    cuisine: String,
    calories: Number,
    ingredients: Array,
    img: String
})

</script>

<style>
    *{
        margin: 0;
        padding: 0;
    }
    img{
        border-radius: 25px 25px 0 0;
    }
    h1{
        font-size: 16px;
        line-height: 19.36px;
        margin-top: 12px;
        padding-bottom: 2.5px;
        font-weight: 700;
    }
    p{
        font-size: 12px;
        line-height: 14.52px;
        padding-bottom: 7.5px;
    }
    .card{
        width: 224px;
        height: 443px;
        border-radius: 25px;
        border: 1px solid #E4E4E4;
        box-shadow: 0px 4px 4px 0px #00000040;


        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: start;

        margin-bottom: 100px;
    }
    .cardInfo{
        margin-top: 4px;
        width: 144px;
        align-self: baseline;
        margin-left: 14px;

    }
    .cardIngredients{
        margin-top: 16px;
        width: 200px;
        height: 118px;
        overflow-y: scroll;
        align-self: baseline;
        font-size: 12px;
        font-weight: 700;
    }
    ul{
        font-weight: 400;
        margin-left: 18px;
        font-size: 12px;
    }
</style>