<template>
  <v-layout
    column
    justify-center
    align-center>
    <v-flex
      xs12
      sm8
      md6>
      <m-table
        :columnNames="employeeColumnNames"
        :tableRows="employees"/>
    </v-flex>
  </v-layout>
</template>

<script>
import table from '../components/table'

export default {
  async asyncData({$axios}) {
    const employees = await $axios
      .get('http://dummy.restapiexample.com/api/v1/employees')
      .then(({data}) => {
        return data.data;
      })
      .catch((error) => {
        return {};
      });

    return {
      employees,
    }
  },
  data() {
    return {
      employeeColumnNames: [
        {
          text: 'id',
          value: 'id'
        },
        {
          text: 'name',
          value: 'employee_name'
        },
        {
          text: 'Salary',
          value: 'employee_salary'
        },
        {
          text: 'Age',
          value: 'employee_age'
        },
        {
          text: 'Image',
          value: 'profile_image',
        },
      ],
    };
  },
  components: {
    'm-table': table,
  },
};
</script>
