<template>
    <div class='col-md-4'>
        <h4>Item list</h4>
        <ul>
            <ListItem 
                v-for="item in items"
                :key="item.etag"
                :item="item"
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
       
}
</script>>

<style scoped>

</style>>