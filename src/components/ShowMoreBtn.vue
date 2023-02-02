<template>
    <div v-if="hide" class="show-more-btn"></div>

    <div v-else class="show-more-btn" @click="more">
        <div class="btn">
            <div class="icon">
                <img src="@/assets/show_more.svg" alt="">
            </div>
            <span class="text">
                Показать ещё
            </span>
        </div>
    </div>
</template>

<script>
import { mapGetters } from 'vuex'


export default {
    computed: {
        ...mapGetters([
            'getAmount',
            'employees'
        ]),

        hide() {
            return this.getAmount > this.employees.length
        }
    },

    methods: {
        more() {
            this.$store.commit('increaseAmount')
        }
    }

}
</script>

<style lang="scss" scoped>
.show-more-btn {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0px;

    width: 1123px;
    height: 46px;


    /* Inside auto layout */

    flex: none;
    order: 3;
    align-self: stretch;
    flex-grow: 0;
}

.show-more-btn:hover {
    cursor: pointer;
}

.btn {

    box-sizing: border-box;

    /* Auto layout */

    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 14px 24px;
    gap: 10px;

    width: 186px;
    height: 46px;

    /* blue */

    border: 1px solid #2A358C;
    /* button_blue */

    filter: drop-shadow(0px 10px 20px rgba(42, 53, 140, 0.2));
    border-radius: 4px;

    /* Inside auto layout */

    flex: none;
    order: 0;
    flex-grow: 0;
}

.text {
    font-style: normal;
    font-weight: 500;
    font-size: 15px;
    line-height: 120%;
    /* identical to box height, or 18px */

    display: flex;
    align-items: center;

    /* blue */

    color: #2A358C;


    /* Inside auto layout */

    flex: none;
    order: 1;
    flex-grow: 0;
}
</style>