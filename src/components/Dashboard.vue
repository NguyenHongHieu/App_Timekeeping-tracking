<template>
  <div id="dashboard">
    <ul class="collection with-header">
      <li class="collecion-header">
        <h4>Employees</h4>
      </li>
      <li
        v-for="employee in employees"
        v-bind:key="employee.id"
        class="collection-item"
      >
        <div class="chip">{{ employee.dept }}</div>
        {{ employee.employee_id }}:{{ employee.name }}
        <router-link
          class="secondary-content"
          v-bind:to="{
            name: 'view-employee',
            params: { employee_id: employee.employee_id },
          }"
        >
          <i class="fa fa-eye"></i>
        </router-link>
      </li>
    </ul>
    <!-- <h3>dashboard</h3> -->
    <div class="fixed-action-btn">
      <router-link to="/new" class="btn-floating btn-large red">
        <i class="fa ca-plus"></i>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "dashboard",
	props: {
		employees: Array
	},
	data() {
		return{
			employees_hc: []
		}
	},
	watch: {
		employees(val){
			val.forEach(emp => {
				if(emp.dept === "Hành chính")
					this.employees_hc.push(emp)
			});
		}
	}
};
</script>

