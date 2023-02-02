<template>
    <div class="tag__item" @click="activate" :style="itemStyle">
        <span :style="spanStyle"> {{ tag.title }} </span>
    </div>
</template>

<script>

export default {
    props: ['tag', 'all'],

    data() {
        return {
            isActive: false
        }
    },

    computed: {
        itemStyle() {
            if (this.isActive) {
                return `
            background: ${this.tag.color};
            border: 1px solid ${this.tag.color};
            `
            } else {
                return `
            background: ${this.tag.backgroundColor};
            border: 1px solid ${this.tag.color};
            `
            }
        },
        spanStyle() {
            if (this.isActive) {
                return `color: white`

            } else {
                return `color: ${this.tag.color}`
            }
        }

    },

    methods: {
        activate() {
            this.isActive = !this.isActive

            this.$emit('activeTags', this.tag.id)

        }
    },

    watch: {
        all(val) {
            if (val) {
                this.isActive = false
            }
        }
    }
}
</script>

<style scoped>

</style>