<template>
    <div class="craft-container">
        <div class="craft-items">
            <div class="craft-item">
                <div v-if="firstItem">
                    {{firstItem.name}}
                    <!--<img :src="firstItem.icon"/>-->
                </div>
                
                <button v-if="firstItem" @click="$emit('onRemoveItem', firstItem)">X</button>
            </div>
            <div class="craft-item">
                {{secondItem ? secondItem.name : ""}}
                <button v-if="secondItem" @click="$emit('onRemoveItem', secondItem)">X</button>
            </div>
        </div>
        <Button @click="$emit('onCombine')" size="small" :disabled="!firstItem || !secondItem">Combiner</Button>
    </div>
</template>

<script>
import Button from "./Button.vue"
export default {
    props: [
        "firstItem",
        "secondItem"
    ],
    components: {
        Button
    }
}
</script>

<style scoped>
    .craft-items {
        @apply
        flex
        mb-2
        bg-gray-200
        rounded-lg
        shadow;
    }
    .craft-item {
        @apply
        w-20
        h-20
        m-2
        p-4
        bg-gray-600;
    }
    .craft-item-img {
        @apply
        h-full
        w-full;
    }
</style>