<template>
    <div class="container">
        <SearchBar @valueSubmit="onValueSubmit"/>
        <div class="row">
            <ItemDetail />
            <ItemList :items="items"/>
        </div>
    </div>
</template>

<script>
import SearchBar from './components/SearchBar';
import ItemList from './components/ItemList';
import ItemDetail from './components/ItemDetail';
import axios from 'axios';


// API KEY
const API_KEY = "";

export default {
    name: "App",
    components: {
        SearchBar,
        ItemList,
        ItemDetail,
    },
    data () {
        return {
            items: [],
            selectedItem: null,
        };
    },
    methods: {
        onValueSubmit(value) {
            axios.get("https://www.googleapis.com/youtube/v3/search", {
                params: {
                    key: API_KEY,
                    type: "video",
                    part: "snippet",
                    q: value
                }
            }).then( response => {
                this.items = response.data.items;
            }).catch(err => {
                // fake data
                console.log(err);
                this.items = [
                    {
                        snippet: {
                            title: "Fake Data Ttile",
                            thumbnails: {
                                default: {
                                    url: "https://upload.wikimedia.org/wikipedia/commons/f/f1/Vue.png",
                                },
                            },
                        },
                        id: {
                            videoId: "test1234455"
                        },
                        etag: "thisisuniqueid",
                    },
                ]
            });
        },
    }
}
</script>

<style scoped>

</style>>