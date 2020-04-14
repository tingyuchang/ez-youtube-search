<template>
    <div class="container">
        <SearchBar @valueSubmit="onValueSubmit"/>
        <div class="row">
            <ItemDetail :item="selectedItem"/>
            <ItemList :items="items" @itemSelect="onItemSelect"/>
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
                            description: "this fake description xxxcc  klffkfhhwqhfkwwfl.",
                            thumbnails: {
                                default: {
                                    url: "https://hinetcdn.waca.ec/uploads/shops/506/products/73/733c0cdeae796f4bb2265e6de4d8df46.jpg",
                                },
                            },
                        },
                        id: {
                            videoId: "test1234455"
                        },
                        etag: "thisisuniqueid-1",
                    },
                    {
                        snippet: {
                            title: "Fake Data Ttile 2",
                            description: "this fake description xxxcc  klffkfhhwqhfkwwfl.",
                            thumbnails: {
                                default: {
                                    url: "https://upload.wikimedia.org/wikipedia/commons/f/f1/Vue.png",
                                },
                            },
                        },
                        id: {
                            videoId: "test1234456"
                        },
                        etag: "thisisuniqueid-2",
                    },
                ]
            });
        },
        onItemSelect(item) {
            this.selectedItem = item;
            console.log(this.selectedItem);
        }
    }
}
</script>

<style scoped>

</style>>