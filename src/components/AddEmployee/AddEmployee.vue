
<template>
  <form class="employee-form">
    <div class="input-group">
      <input type="text" name="full_name" v-model="employee.full_name">
      <label for="full_name"> ФИО </label>
    </div>

    <div class="input-group">
      <input type="text" name="inn" v-model="employee.inn">
      <label for="inn"> ИНН </label>
    </div>

    <div class="input-group">

      <input type="text" name="address" v-model="employee.address">
      <label for="adress"> Адрес</label>
    </div>

    <div class="input-group">

      <input type="text" name="passport" v-model="employee.passport">
      <label for="passport"> Адрес</label>
    </div>

    <div class="input-group">
      <input type="date" name="birth" id="" v-model="employee.birth">
      <label for="birth">Дата рождения</label>
    </div>

    <div class="input-group">

      <input type="number" name="age" id="" v-model="employee.age">
      <label for="age">Возраст</label>
    </div>

    <div class="input-group">
      <select name="type_contract" id="" v-model="employee.type_contract">
        <option disabled selected> --- </option>
        <option v-for="type_contract in type_contracts" :value="type_contract" :key="type_contract.id"> {{
          type_contract.title
        }}
        </option>
      </select>
      <label for="type_contract">Тип контракта</label>
    </div>

    <div class="input-group">
      <select name="gender" id="" v-model="employee.gender">
        <option disabled selected> --- </option>
        <option v-for="gender in genders" :value="gender" :key="gender.id"> {{ gender.title }}</option>
      </select>
      <label for="gender">Пол</label>
    </div>

    <div class="input-group">

      <select name="country" id="" v-model="employee.country">
        <option selected disabled>---</option>
        <option v-for="country in countries" :value="country" :key="country.id"> {{ country.title }}</option>
      </select>
      <label for="country">Гражданство</label>
    </div>

    <div class="input-group">

      <select name="position" id="" v-model="employee.position">
        <option selected disabled>---</option>
        <option v-for="position in positions" :value="position" :key="position.id">{{ position.name }}</option>
      </select>
      <label for="position">Должность</label>
    </div>

    <div class="input-group">
      <select name="tag" id="" v-model="employee.status.tag">
        <option selected disabled>---</option>
        <option v-for="tag in stuff_tags" :value="tag" :key="tag.id"> {{ tag.title }}</option>
      </select>
      <label for="tag">Статус</label>
    </div>

    <div class="input-group">
      <input type="text" name="description" v-model="employee.status.description">
      <label for="description">Описание статуса</label>
    </div>

    <add-btn @click="addEmployee" />

    <router-link :to="{ name: 'home' }">К списку</router-link>


  </form>
</template>

<script>
import { mapGetters } from 'vuex';
import AddBtn from '@/components/Buttons/AddBtn.vue';
export default {
  components: { AddBtn },
  data() {
    return {
      employee: {
        status: {}
      }

    }
  },

  computed: {
    ...mapGetters([
      'type_contracts',
      'genders',
      'countries',
      'positions',
      'stuff_tags'
    ])
  },

  methods: {
    addEmployee() {
      for (let key in this.employee) {
        if (typeof this.employee[key] === 'object' && key !== 'status') {
          this.employee[`${key}_id`] = this.employee[key].id
        }
      }

      this.$store.commit('addEmployee', this.employee)
      this.employee = {}
      this.employee.status = {}
    }
  }

}
</script>

<style  scoped>
input,
select {
  background: #E8F1F4;
  border: 1px solid #E0EBEF;
  border-radius: 0;
}

.employee-form {
  display: grid;
  width: 600px;
  justify-content: left;
  padding: 10px;
}

.employee-form>div {
  margin: 2px
}

.input-group {
  float: right;
}



.btn>span {
  color: #FFFFFF;
  margin-left: 10px;
}
</style>