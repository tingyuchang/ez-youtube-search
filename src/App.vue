<template>
    <div class="container">
        <SearchBar />
        <div class="row">
            <ItemDetail />
            <ItemList />
        </div>
    </div>
</template>

<script>
import SearchBar from './components/SearchBar';
import ItemList from './components/ItemList';
import ItemDetail from './components/ItemDetail';

export default {
    name: "App",
    components: {
        SearchBar,
        ItemList,
        ItemDetail,
    },
}
</script>

<style scoped>

</style>>