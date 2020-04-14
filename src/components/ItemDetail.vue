<template>
    <div v-if="item" class="col-md-8">
        <div class="embed-responsive embed-responsive-16by9">
            <iframe class="embed-responsive-item" :src="videoUrl" />
        </div>
        <div class="details">
            <h4>{{ item.snippet.title}}</h4>
            <p>{{ item.snippet.description }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "ItemDetail",
    props: ['item'],
    computed: {
        videoUrl() {
            const { videoId } = this.item.id;
            return `https://www.youtube.com/embed/${videoId}`;
        }
    }
}
</script>>

<style scoped>
    .details {
        margin-top: 10px;
        padding: 10px;
        border: 1px solid #ddd;
        border-radius: 4px;
    }
</style>>