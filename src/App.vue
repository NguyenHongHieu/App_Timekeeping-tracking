<template>
  <div id="app">
    <navbar/>
    <div class="container"></div>
    <new-employee />
    <dashboard :employees = employees />
    <!-- <router-view /> -->
  </div>
</template>

<script>
import db from "./firebase/firebaseInit";
import Navbar from './components/Navbar'
import Dashboard from './components/Dashboard.vue'
import NewEmployee from './components/NewEmployee.vue';
export default {
  name: 'App', 
  components: {
    Navbar,
    Dashboard,
    NewEmployee
  },
  data() {
    return {
      employees: [],
    };
  },
	methods: {
		getEmployees() {
			db.collection("employees") 
      	// .orderBy("dept")
      	.get()
				.then(snap => {
					snap.forEach(doc => {
						this.employees.push(doc.data())
					})
				});
		}
	},
  created() {
		this.getEmployees();
  },
}
</script>




