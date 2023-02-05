<template>
    <div class="search">
        <div class="input">
            <input class="search__input" type="text" placeholder="Поиск сотрудника">
        </div>
        <span class="tip">Например, Иванов Иван</span>
    </div>
</template>

<script>
export default {

}
</script>

<style  scoped>
.search {
    /* top_bar_search */


    box-sizing: border-box;

    /* Auto layout */

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    padding: 0px 30px 30px;
    gap: 10px;

    width: 1203px;
    height: 102px;

    /* white */

    background: #FFFFFF;
    /* line */

    border-bottom: 1px solid #DBE4ED;

    /* Inside auto layout */

    flex: none;
    order: 0;
    align-self: stretch;
    flex-grow: 0;
}

.input {
    /* form */


    /* Auto layout */

    display: flex;
    flex-direction: row;
    align-items: flex-start;
    padding: 0px;

    width: 1143px;
    height: 46px;


    /* Inside auto layout */

    flex: none;
    order: 0;
    align-self: stretch;
    flex-grow: 0;
}

input {
    /* display: flex;
    flex-direction: row;
    align-items: flex-start;
    padding: 0px;

    width: 1143px;
    height: 46px;

    box-sizing: border-box; */

    /* Auto layout */

    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 12px 16px;
    gap: 10px;

    width: 1143px;
    height: 46px;

    background: #E8F1F4;
    border: 1px solid #E0EBEF;
    border-radius: 4px;

    /* Inside auto layout */

    flex: none;
    order: 0;
    flex-grow: 1;

}

.tip {
    width: 170px;
    height: 16px;

    font-style: normal;
    font-weight: 400;
    font-size: 13px;
    line-height: 120%;
    /* identical to box height, or 16px */

    display: flex;
    align-items: center;

    /* grey */

    color: #B0BCC7;


    /* Inside auto layout */

    flex: none;
    order: 1;
    flex-grow: 0;
}

.search__input {
    background-image: url('@/assets/Search.svg');
    background-repeat: no-repeat;
    background-position: 99% center;
}
</style>