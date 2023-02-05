<template>
  <div class="container">
    <div class="body">
      <EmployeeSearch />
      <EmployeeList />
    </div>
    <div class="aside">
      <div class="btn__wrapper">
        <add-btn @click="route" />
      </div>
      <EmployeeFilter />
    </div>
  </div>

</template>

<script>
import EmployeeSearch from '@/components/Search/EmployeeSearch.vue';
import EmployeeList from '@/components//EmployeesList/EmployeeList.vue';
import EmployeeFilter from '@/components/Filter/EmployeeFilter.vue';
import AddBtn from '@/components/Buttons/AddBtn.vue';

export default {
  components: {
    EmployeeList,
    EmployeeSearch,
    EmployeeFilter,
    AddBtn,
  },

  methods: {
    route() {
      this.$router.push('add-employee')
    }
  }

}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 0px;
  gap: 30px;

  width: 1820px;
  /* height: 1202px; */
  /* height: auto; */



  /* Inside auto layout */

  /* flex: none; */
  order: 0;
  flex-grow: 1;
}

.body {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 30px 0px;

  /* height: auto; */

  width: 1203px;
  /* height: 1202px; */

  /* white */

  background: #FFFFFF;
  /* cart_big */

  box-shadow: 0px 7px 30px rgba(42, 53, 140, 0.03);

  /* Inside auto layout */

  /* flex: none; */
  order: 0;
  flex-grow: 1;
  align-self: stretch;

}

.aside {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 0px;
  gap: 30px;

  width: 587px;
  height: 647px;

  /* white */

  background: #FFFFFF;
  /* cart_big */

  box-shadow: 0px 7px 30px rgba(42, 53, 140, 0.03);
  border-radius: 10px;

  /* Inside auto layout */

  flex: none;
  order: 1;
  flex-grow: 1;
}

.btn__wrapper {
  /* btn */


  box-sizing: border-box;

  /* Auto layout */

  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 30px;
  gap: 10px;

  width: 587px;
  height: 124px;

  /* line */

  border-bottom: 1px solid #DBE4ED;

  /* Inside auto layout */

  flex: none;
  order: 0;
  align-self: stretch;
  flex-grow: 0;
}
</style>
