<template>
    <div class="cart">
        <div class="main__info">
            <div class="main__name">
                {{ employee.full_name }}
            </div>
            <div class="main__inn">
                <span>ИНН {{ employee.inn }}</span>
            </div>
            <div class="main__position">
                <div class="position__frame">
                    <div class="contract">
                        <span class="contract__slug">{{ employee.type_contract.slug }}</span>
                    </div>
                </div>
                <span class="position__name">
                    {{ employee.position.name }}
                </span>
            </div>
        </div>
        <div class="additional-info">
            <div class="passport">
                <img class="country-icon" :src="employee.country.icon" alt="">
                <span class="country-slug"> {{ employee.country.slug }}</span>
                <span class="passport-number"> {{ employee.passport }}</span>
            </div>
            <div class="line"></div>
            <span class="additional-text">{{ employee.address }}</span>
            <div class="line"></div>
            <span class="additional-text">Дата рождения: {{ employee.birth }}</span>
            <div class="line"></div>
            <span class="additional-text">Возраст: {{ employee.age }} год(а)</span>
            <div class="line"></div>
            <span class="additional-text">Пол: {{ employee.gender.title }} </span>
        </div>
        <div class="label" :style="`background: ${employee.status.tag.color};`">
            <span>{{ employee.status.description }} </span>
        </div>
    </div>
</template>

<script>
export default {
    props: ['employee']
}
</script>

<style lang="scss" scoped>
.cart {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: flex-start;
    padding: 25px;
    gap: 15px;

    width: 1123px;
    height: 150px;

    /* light_grey */

    background: #E7F3FF;
    border-radius: 4px;

    /* Inside auto layout */

    flex: none;
    order: 0;
    flex-grow: 0;
}

.main__info {
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 0px;
    gap: 20px;

    width: 1073px;
    height: 24px;


    /* Inside auto layout */

    flex: none;
    order: 0;
    align-self: stretch;
    flex-grow: 0;
}

.additional__info {
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 0px;
    gap: 15px;

    width: 1073px;
    height: 18px;


    /* Inside auto layout */

    flex: none;
    order: 1;
    align-self: stretch;
    flex-grow: 0;
}



.main {

    &__name {
        display: inline-flex;
        // width: 502px;
        height: 22px;

        font-style: normal;
        font-weight: 600;
        font-size: 18px;
        line-height: 120%;
        /* identical to box height, or 22px */


        /* blue */

        color: #2A358C;


        /* Inside auto layout */

        flex: none;
        order: 0;
        flex-grow: 0;
    }

    &__inn {
        display: inline-flex;
        flex-direction: row;
        align-items: flex-start;
        padding: 4px 8px;
        gap: 10px;

        // width: 128px;
        height: 24px;

        /* white */

        background: #FFFFFF;
        border-radius: 4px;

        /* Inside auto layout */

        flex: none;
        order: 1;
        flex-grow: 0;

        span {
            // display: inline-flex;
            height: 16px;

            font-style: normal;
            font-weight: 500;
            font-size: 13px;
            line-height: 120%;
            /* identical to box height, or 16px */


            /* dark_grey */

            color: #84909B;


            /* Inside auto layout */

            flex: none;
            order: 0;
            flex-grow: 0;
        }
    }

}

.main {

    &__position {
        display: inline-flex;
        flex-direction: row;
        align-items: center;
        padding: 0px;
        gap: 10px;

        width: 251px;
        height: 24px;


        /* Inside auto layout */

        flex: none;
        order: 2;
        flex-grow: 0;
    }
}

.position {

    &__frame {
        display: inline-flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        padding: 4px;
        gap: 10px;

        width: 39px;
        height: 24px;

        /* green */

        background: #00AE5B;
        border-radius: 4px;

        /* Inside auto layout */

        flex: none;
        order: 0;
        flex-grow: 0;
    }

    &__name {
        // width: 300px;
        height: 17px;

        font-style: normal;
        font-weight: 400;
        font-size: 14px;
        line-height: 120%;
        /* identical to box height, or 17px */


        /* black */

        color: #041423;




        flex: none;
        order: 1;
        flex-grow: 0;
    }
}

.contract {

    &__slug {


        width: 31px;
        height: 16px;

        font-style: normal;
        font-weight: 600;
        font-size: 13px;
        line-height: 120%;
        /* identical to box height, or 16px */


        /* white */

        color: #FFFFFF;


        /* Inside auto layout */

        flex: none;
        order: 0;
        flex-grow: 0;
    }
}

.additional-info {
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 0px;
    gap: 15px;

    width: 1073px;
    height: 18px;

}

.passport {
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 0px;
    gap: 10px;

    width: 160px;
    height: 18px;
}

.country-icon {
    width: 20px;
    height: 14px;

    border-radius: 2px;
}

.country-slug {
    font-style: normal;
    font-weight: 400;
    font-size: 14px;
    line-height: 130%;
    /* or 18px */


    /* black */

    color: #041423;
}

.passport-number {
    // width: 100px;
    font-style: normal;
    font-weight: 400;
    font-size: 14px;
    line-height: 130%;
    /* or 18px */


    /* black */

    color: #041423;
}

.line {
    width: 16px;
    height: 0px;

    /* line_2 */

    border: 1px solid #CEDAE6;
    transform: rotate(-90deg);
}

.additional-text {
    // width: 191px;
    height: 18px;

    // font-family: 'Montserrat';
    font-style: normal;
    font-weight: 400;
    font-size: 14px;
    line-height: 130%;
    /* or 18px */


    /* black */

    color: #041423;
}

.label {
    display: inline-flex;
    flex-direction: row;
    align-items: flex-start;
    padding: 4px 8px;
    gap: 10px;

    // width: 201px;
    // height: 28px;

    border-radius: 4px;

    /* Inside auto layout */

    // flex: 'flex-grow';
    order: 3;
    // flex-grow: 1;

    span {
        // display: inline-flex;
        // width: 185px;
        // height: 17px;

        font-style: normal;
        font-weight: 500;
        font-size: 14px;
        line-height: 120%;
        /* identical to box height, or 17px */


        /* white */

        color: #FFFFFF;


        /* Inside auto layout */

        // flex: none;
        // order: 0;
        // flex-grow: 0;
    }
}
</style>