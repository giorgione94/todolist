<template>
    <div class="container">
        <div class="heading">
            <h2 id="title">Todo List</h2>
            <add-item-form-vue
            v-on:reloadlist="getList()"/>
        </div>
        <div>
            <list-view-vue 
            :items="items" 
            v-on:reloadlist="getList()" 
            />
        </div>
    </div>
</template>

<script>
import AddItemFormVue from './AddItemForm.vue';
import ListViewVue from './ListView.vue';
export default {
    components: {
        AddItemFormVue,
        ListViewVue
    },
    data: function () {
        return {
            items: []
        }
    },
    methods: {
        getList() {
            axios.get('api/items')
                .then(response => {
                    this.items = response.data
                })
                .catch(error => {
                    console.log(error);
                })
        }
    },
    created() {
        this.getList();
    }
}
</script>

<style>
.container {
    width: 350px;
    margin: auto;
}

.heading {
    background-color: aquamarine;
    padding: 10px;
}

#title {
    text-align: center;
}
</style>