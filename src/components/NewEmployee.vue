<template>
  <div id="new-employee">
    <h3>New Employee</h3>
    <form @submit.prevent="addEmployee()">
			<input type="number" ref="emp_id" placeholder="ID">
			<input type="text" ref="name" placeholder="Name">
			<input type="text" ref="dept" placeholder="Dept">
			<input type="text" ref="pos" placeholder="Position">
			<input type="submit">
		</form>
  </div>
</template>

<script>
import db from "../firebase/firebaseInit";
export default {
  name: "new-employee",
  data() {
    return {};
  },
	methods: {
		addEmployee(){
			db.collection('employees')
				.add({
						"employee_id" : this.$refs.emp_id.value,
						"name" : this.$refs.name.value,
						"dept" : this.$refs.dept.value,
						"position": this.$refs.pos.value,
					}
				)
		}
	}
};
</script>

