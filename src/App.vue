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
                            title: "Gundam vs Hello Kitty",
                            description: `鋼彈和Hello Kitty在宇宙相遇並互相了解的原創故事的完整版本
官方網站：https://www.gundamvskitty.com
官方推特：https://twitter.com/gundamvskitty

【動畫製作主要工作人員】
導演/分鏡：林 嘉姫
作畫監督：山岸正和、山村直己、壽司
美術監督：金子雄司
色彩設計：安部渚
攝影監督：川下裕樹
編輯：新居和弘
音響監督：藤野貞義
音響效果：西村睦弘

監修/協力：三麗鷗股份有限公司`,
                            thumbnails: {
                                default: {
                                    url: "https://hinetcdn.waca.ec/uploads/shops/506/products/73/733c0cdeae796f4bb2265e6de4d8df46.jpg",
                                },
                            },
                        },
                        id: {
                            videoId: "oswjHj6V_xs"
                        },
                        etag: "thisisuniqueid-1",
                    },
                    {
                        snippet: {
                            title: "Age of Empires II DE - E3 2019 - Gameplay Trailer",
                            description: `Age of Empires II: Definitive Edition releases 2019 and will be available with Xbox Game Pass for PC. 

Age of Empires II: Definitive Edition celebrates the 20th anniversary of one of the most popular strategy games ever with stunning 4K Ultra HD graphics, remastered audio and a whole new campaign - The Last Khans. Return to Reign in 2019.

Learn more: https://www.xbox.com/games/age-of-emp...

Subscribe to Xbox:
🎮: https://xbx.lv/2EEjmaR

FOLLOW XBOX:
Facebook: https://www.facebook.com/Xbox   
Twitter: https://www.twitter.com/Xbox   
Instagram: https://www.instagram.com/Xbox

Audio Description: https://youtu.be/1XlHqf_k6-c`,
                            thumbnails: {
                                default: {
                                    url: "https://cdn.unwire.hk/wp-content/uploads/2019/06/aoe-1280x710.png",
                                },
                            },
                        },
                        id: {
                            videoId: "ZOgBVR21pWg"
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