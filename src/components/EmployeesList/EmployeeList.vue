<template>
    <div class="list__wrapper">
        <h1>Список сотрудников</h1>
        <TagsList />
        <carts-list />
        <show-more-btn />

    </div>
</template>

<script>
import { mapGetters } from 'vuex';
import TagsList from '@/components/Tags/TagsList.vue';
import CartsList from './CartsList.vue';
import ShowMoreBtn from '@/components/Buttons/ShowMoreBtn.vue';

export default {
    components: {
        TagsList,
        CartsList,
        ShowMoreBtn
    },

    computed: {
        ...mapGetters([
            'stuff_tags'
        ])
    }

}
</script>

<style scoped>
.list__wrapper {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding: 30px 40px;
    gap: 20px;

    width: 1203px;
    /* height: 1040px; */


    /* Inside auto layout */

    flex: none;
    order: 1;
    align-self: stretch;
    flex-grow: 1;
}

h1 {
    width: 289px;
    height: 31px;

    /* H1 */

    font-style: normal;
    font-weight: 600;
    font-size: 26px;
    line-height: 120%;
    /* or 31px */

    display: flex;
    align-items: center;

    /* black */

    color: #041423;


    /* Inside auto layout */

    flex: none;
    order: 0;
    flex-grow: 0;
}
</style>