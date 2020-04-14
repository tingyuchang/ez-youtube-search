<template>
    <div class='col-md-4'>
        <h4>Item list</h4>
        <ul class="list-group">
            <ListItem 
                v-for="item in items"
                :key="item.etag"
                :item="item"
                @itemSelect="onItemSelect"
            />

        </ul>
    </div>
</template>>

<script>
import ListItem from './ListItem';

export default {
    name: "ItemList",
    components: {
        ListItem,
    },
    props: {
        items: Array,
    },
    methods: {
        onItemSelect(item) {
            this.$emit("itemSelect", item);
        },
    }, 
}
</script>>

<style scoped>

</style>>