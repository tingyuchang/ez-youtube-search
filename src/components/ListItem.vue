<template>
    <li class="list-group-item" @click="onItemSelect">
        <img class="align-self-center mr-3" :src="thumbnailUrl"/>
        <div class="media-body">
            {{ item.snippet.title }}
        </div>
    </li>
</template>

<script>
export default {
    name: "ListItem",
    props: ['item'],
    computed: {
        thumbnailUrl() {
            return this.item.snippet.thumbnails.default.url;
        }
    },
    methods: {
        onItemSelect() {
            this.$emit("itemSelect", this.item);
        }
    }
}
</script>>

<style scoped>
    li {
        display: flex;
        cursor: pointer;
    }
    li:hover {
        background-color: #eee;
    }
    img {
        width: 64px;
        height: 64px;
    }
</style>