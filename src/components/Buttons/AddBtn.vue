<template>
    <button class="btn" @click.prevent="click">
        <img src="@/assets/Add_icon.svg" alt="">
        <span>Добавить нового сотрудника</span>
    </button>
</template>

<script>
export default {
    methods: {
        click() {
            this.$emit('click')
        }
    }

}
</script>

<style scoped>
.btn {
    /* .base */


    /* Auto layout */

    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 20px 34px;
    gap: 10px;

    width: 527px;
    height: 64px;

    /* light_blue */

    background: #00B6ED;
    /* button_light_blue */

    box-shadow: 0px 10px 20px rgba(0, 182, 237, 0.2);
    border-radius: 4px;

    /* Inside auto layout */

    flex: none;
    order: 0;
    flex-grow: 1;
}


span {
    /* Кнопка */


    width: 308px;
    height: 24px;

    font-style: normal;
    font-weight: 500;
    font-size: 20px;
    line-height: 120%;
    /* identical to box height, or 24px */

    display: flex;
    align-items: center;

    /* white */

    color: #FFFFFF;


    /* Inside auto layout */

    flex: none;
    order: 1;
    flex-grow: 0;

}
</style>