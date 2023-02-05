<template>
    <div class="list__carts">
        <employee-cart v-for="employee in computedEmployees" :key="employee.id" :employee="employee" />
    </div>
</template>

<script>
import EmployeeCart from '@/components/EmployeesList/EmployeeCart.vue'
import { mapGetters } from 'vuex';
export default {
    components: { EmployeeCart },

    computed: {
        ...mapGetters([
            'employees',
            'getFilter',
            'getTags',
            'getAmount',
            'isFiltred'

        ]),

        computedEmployees() {
            let result = [...this.employees]
            if (this.isFiltred) {
                result = this.employees.filter(item => item.country_id === this.getFilter.country_id ||
                    item.gender_id === this.getFilter.gender_id ||
                    item.position_id === this.getFilter.position_id ||
                    this.getFilter.contract.includes(item.type_contract_id)
                )
            }

            if (this.getTags.length) {
                result = result.filter(item => this.getTags.includes(item.status.tag_id))
            }

            this.$store.commit('setComputedLength', result.length)


            result = result.filter((item, index) => index <= this.getAmount)

            // this.$store.commit('setComputedLength', result.length)

            return result
        }
    }

}
</script>

<style lang="scss"  scoped>
.list__carts {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    padding: 0px;
    gap: 15px;

    width: 1123px;
    // height: 810px;


    /* Inside auto layout */

    flex: none;
    order: 2;
    flex-grow: 0;
}
</style>