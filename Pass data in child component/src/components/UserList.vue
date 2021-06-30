<template>
  <b-card :title="ComponentTitle" img-alt="Image" img-top tag="article">
    <b-card-body>
        <div v-html="html" class="mb-4"></div>
      User List Component
      <b-container fluid>
        <ul>
          <li
            class="pointer"
            v-for="user in users"
            :key="user.id"
            v-on:click="userSelected($event, user.id)"
          >
            id: {{ user.id }}, name: {{ user.name }} salary is - actual value
            {{ user.salary }} -converted value
            {{ user.salary | convertToSalary | addCurrency }}
          </li>
        </ul>
      </b-container>
    </b-card-body>
  </b-card>
</template>
<script>
export default {
  props:['ComponentTitle', 'html'],
  data() {
    return {
      users: [
        { id: 1, name: "Steve", salary: 12 },
        { id: 2, name: "Ram", salary: 10 },
        { id: 3, name: "Leonidas", salary: 8 },
      ],
    };
  },
  filters: {
    convertToSalary: function (value) {
      return `${value * 1000}.00/-`;
    },
    addCurrency: function (value) {
      return `$ ${value}`;
    },
  },
};
</script>