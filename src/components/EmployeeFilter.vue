<template>
    <div class="filter__wrapper">
        <h1>Фильтр</h1>
        <div class="input__row">
            <div class="input__group">
                <span class="input__title">
                    Гражданство
                </span>
                <select class="input__select" name="country" id="" v-model="filter.country_id">
                    <option disabled selected :value="0"> Все страны </option>
                    <option v-for="country in countries" :value="country.id" :key="country.id"> {{ country.title }}
                    </option>
                </select>

            </div>
            <div class="input__group">
                <span class="input__title">
                    Пол
                </span>
                <select class="input__select" name="gender" id="" v-model="filter.gender_id">
                    <option disabled selected :value="0"> Без разницы </option>
                    <option v-for="gender in genders" :value="gender.id" :key="gender.id"> {{ gender.title }}
                    </option>
                </select>
            </div>
        </div>
        <div class="input__row">
            <div class="input__group">
                <span class="input__title">
                    Должность
                </span>
                <select class="input__select long" name="position" id="" v-model="filter.position_id">
                    <option disabled selected :value="0"> Все должности </option>
                    <option v-for="position in positions" :value="position.id" :key="position.id"> {{ position.name }}
                    </option>
                </select>
            </div>
        </div>
        <div class="input__row">
            <div class="col">
                <div class="input__group">
                    <span class="input__title">
                        Тип договора
                    </span>
                    <div class="checkbox__row" v-for="contract in type_contracts" :key="contract.id">
                        <input class="checkbox__box" type="checkbox" :value="contract.id" :name="contract.slug"
                            v-model="filter.contract">
                        <label class="checkbox__label" :for="contract.slug"> {{ contract.slug }}</label>
                    </div>
                </div>
            </div>
        </div>

        <div class="input__row">
            <button class="accept" @click.prevent="accept">
                <span>Применить</span>
            </button>
            <button class="clear" @click.prevent="clear">
                <span>Очистить</span>
            </button>

        </div>
    </div>
</template>

<script>
import { mapGetters } from 'vuex';
export default {
    data() {
        return {
            filter: null
        }
    },

    computed: {
        ...mapGetters([
            'type_contracts',
            'countries',
            'genders',
            'positions',
            'getFilter'
        ])
    },

    methods: {
        accept() {
            this.$store.commit('setFilter', this.filter)
            this.$store.commit('filtred')
        },

        clear() {
            this.filter.position_id = this.filter.gender_id = this.filter.country_id = 0
            this.filter.contract = []
            this.$store.commit('setFilter', this.filter)
            this.$store.commit('notFiltred')

        }
    },

    created() {
        this.filter = this.getFilter
    }

}
</script>

<style  scoped>
.filter__wrapper {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding: 0px 30px 30px;
    gap: 20px;

    width: 587px;
    height: 493px;


    /* Inside auto layout */

    flex: none;
    order: 1;
    align-self: stretch;
    flex-grow: 0;
}

h1 {
    font-family: 'Montserrat';
    font-style: normal;
    font-weight: 600;
    font-size: 26px;
    line-height: 120%;
}

.input__row {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    padding: 0px;
    gap: 20px;

    width: 527px;
    height: 74px;


    /* Inside auto layout */

    flex: none;
    order: 1;
    align-self: stretch;
    flex-grow: 0;
}

.input__row:nth-child(4) {
    height: 138px;
}

.input__row:last-child {
    box-sizing: border-box;

    /* Auto layout */

    display: flex;
    flex-direction: row;
    align-items: flex-start;
    padding: 20px 0px 0px;
    gap: 20px;

    width: 527px;
    height: 66px;

    /* line */

    border-top: 1px solid #DBE4ED;

    /* Inside auto layout */

    flex: none;
    order: 4;
    align-self: stretch;
    flex-grow: 0;
}

.input__group {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding: 0px;
    gap: 10px;

    width: 253.5px;
    height: 74px;


    /* Inside auto layout */

    flex: none;
    order: 0;
    flex-grow: 1;
}

select {
    box-sizing: border-box;

    /* Auto layout */

    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 12px 16px;
    gap: 10px;

    width: 253.5px;
    height: 46px;

    background: #E8F1F4;
    border: 1px solid #E0EBEF;
    border-radius: 4px;

    /* Inside auto layout */




    font-family: 'Montserrat';
    font-style: normal;
    font-weight: 400;
    font-size: 15px;
    line-height: 120%;

    color: #84909B;
}



.input__title {
    /* Заголовок */


    width: 253.5px;
    height: 18px;

    font-family: 'Montserrat';
    font-style: normal;
    font-weight: 500;
    font-size: 15px;
    line-height: 120%;
    /* identical to box height, or 18px */

    display: flex;
    align-items: center;

    /* black */

    color: #041423;


    /* Inside auto layout */

    flex: none;
    order: 0;
    align-self: stretch;
    flex-grow: 0;
}

.long {
    width: 527px;
}

.checkbox__row {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    padding: 0px;
    gap: 8px;

    width: 49px;
    height: 20px;
}

.checkbox__box {
    /* checkbox */


    box-sizing: border-box;

    /* Auto layout */

    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 12px 16px;
    gap: 10px;

    width: 20px;
    height: 20px;

    /* white */

    background: #FFFFFF;
    border: 1px solid #DCDCDC;
    border-radius: 4px;

    /* Inside auto layout */

    flex: none;
    order: 0;
    flex-grow: 0;
}

.checkbox__label {
    width: 21px;
    height: 20px;

    font-family: 'Montserrat';
    font-style: normal;
    font-weight: 400;
    font-size: 15px;
    line-height: 135%;
    /* or 20px */

    display: flex;
    align-items: center;

    /* black */

    color: #041423;


    /* Inside auto layout */

    flex: none;
    order: 1;
    flex-grow: 0;
}

button {
    /* button */


    /* Auto layout */

    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 0px;

    width: 253.5px;
    height: 46px;


    /* Inside auto layout */

    flex: none;
    order: 0;
    flex-grow: 1;
}

.accept {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 14px 24px;
    gap: 10px;

    width: 253.5px;
    height: 46px;

    /* green */

    background: #00AE5B;
    box-shadow: 0px 10px 20px rgba(0, 174, 91, 0.2);
    border-radius: 4px;

    /* Inside auto layout */

    flex: none;
    order: 0;
    flex-grow: 1;
}

.clear {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    padding: 14px 24px;
    gap: 10px;

    width: 253.5px;
    height: 46px;

    /* dark_grey */

    background: #84909B;
    box-shadow: 0px 10px 20px rgba(106, 117, 128, 0.2);
    border-radius: 4px;

    /* Inside auto layout */

    flex: none;
    order: 0;
    flex-grow: 1;
}

button>span {
    font-weight: 500;
    font-size: 15px;
    line-height: 120%;
    color: #FFFFFF;
}
</style>