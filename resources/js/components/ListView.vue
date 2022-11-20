<template>
    <div>
        <div v-for="(item, index) in items" :key="index">
            <list-item-vue 
            :item="item" 
            class="item" 
            v-on:itemchanged="$emit('reloadlist')"
            />
        </div>
    </div>
</template>

<script>
import ListItemVue from './ListItem.vue'
export default {
    props: ['items'],
    components: {
        ListItemVue
    }
}
</script>

<style>
.item {
    
    background: #e6e6e6;
    padding: 5px;
    margin-top: 5px;
}
</style>