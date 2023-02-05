<template>
    <div class="tabs">

        <div class="tag__item all" @click="showAll" :style="tagStyle">
            <span :style="spanStyle"> Весь список </span>
        </div>


        <TagItem :tag="tag" v-for="tag in stuff_tags" :key="tag.id" :all="all" @activeTags="activeTags" />

    </div>
</template>

<script>
import TagItem from '@/components/Tags/TagItem.vue';
import { mapGetters } from 'vuex';

export default {
    components: { TagItem },

    data() {
        return {
            all: true,
            selectedTags: []
        }
    },

    computed: {
        ...mapGetters([
            'stuff_tags'
        ]),
        tagStyle() {
            if (this.all) {
                return `background: #B0BCC7;`
            } else {
                return `background: white;`
            }
        },

        spanStyle() {
            if (!this.all) {
                return `color: #B0BCC7;`
            } else {
                return `color: white;`
            }
        },

    },

    methods: {
        showAll() {
            this.all = true
            this.selectedTags = []
            this.$store.commit('setTags', this.selectedTags)

        },

        activeTags(data) {
            this.all = false
            if (this.selectedTags.includes(data)) {
                const index = this.selectedTags.indexOf(data)
                this.selectedTags.splice(index, 1)
            } else {
                this.selectedTags.push(data)
            }
            if (!this.selectedTags.length) this.all = true
            this.$store.commit('setTags', this.selectedTags)
        }
    }
}
</script>

<style >
.tabs {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    padding: 0px;
    gap: 10px;

    width: 1123px;
    height: 33px;


    flex: none;
    order: 1;
    align-self: stretch;
    flex-grow: 0;
}

.tag__item {
    box-sizing: border-box;

    display: inline-flex;
    flex-direction: row;
    align-items: flex-start;
    padding: 8px 15px;


    height: 33px;

    border-radius: 30px;

    flex: none;
    order: 0;
    flex-grow: 0;
}

.all {

    /* grey */

    border: 1px solid #B0BCC7;
}

.all>span {
    color: white;
}



.tag__item:hover {
    cursor: pointer;
}
</style>