<template>
<div>	
	<Header />

	<div class="card position-absolute translate-middle shadow-lg p-3  bg-body" style=" display: block; width: 35rem; height: 35rem; color: black; left:50%; top:45%; margin-top: 3rem; margin-bottom: auto; border-radius: 10px;">
		<div class = "position.position-relative start-0 top-50 text-center fs-4"> Register</div>
		<form @submit.prevent="register">
			<div class="form-floating mb-2 mx-auto" style="width: 85%; margin: 1.5rem;"> 
				<input v-model="user.name" name= "name" type="text" class="form-control" id="nameControl" placeholder="Name" style="border-radius:9px;">
				<label for="nameControl" class="form-label">Name</label>
			</div>
			<div class="form-floating mb-2 mx-auto" style="width: 85%; margin: 1.5rem;"> 
				<input v-model="user.email" name= "email" type="email" class="form-control" id="exampleFormControlInput1" placeholder="Email address" style="border-radius:9px;" >
				<label for="exampleFormControlInput1">Email address</label>
			</div>
			<div class="form-floating mb-2 mx-auto" style="width: 85%; margin: 1.5rem;"> 
				<input v-model="user.password" name="password" type="password" class="form-control" id="floatingPassword" placeholder="Password" style="border-radius:9px;">
				<label for="floatingPassword">Password</label>
			</div>
			<div class="form-floating mb-3 mx-auto" style="width: 85%; margin: 1.5rem;"> 
				<input v-model="passwordConfirmation" type="password" class="form-control" id="floatingPassword2" placeholder="Confirm password" style="border-radius:9px;">
				<label for="floatingPassword2">Confirm password</label>
			</div>
			<button class="position-absolute btn btn-dark translate-middle-x p-2" style="left: 50%; font-size: 18px; margin-top:40px; color: #00FF00;" type="submit">Sign Up</button>
		</form>
	</div>
		
	<Footer/>
</div>
</template>

<script>

import Footer from '@/components/Footer.vue'
import Header from '@/components/Header.vue'
export default {
	components: {
		Footer,
        Header,
	},
	data() {
      return {	
        user: {
			name: '',
			email: '',
			password: '',
        },
		passwordConfirmation: '',
		submitting: true,
		error: false,
		errorMsg: '',	
      }
    },

	methods: {

		validateForm() {

			if (this.user.password !== this.passwordConfirmation) {
			
				return false;
			}
			else if (this.user.password.length < 6) {
				return false;
			}

			return true;
		},

		async register() {
			if (!this.validateForm()) {
				return;
			}
			const exists = await this.$store.dispatch('user/userExists', this.user);
			if (exists) {
				console.log("existe na BD");
			}
			else { //add user to database
				const addedUser = await this.$store.dispatch('user/addUser');
				//this.$store.state.
				console.log(addedUser);
				this.$router.push({ path: '/message/4'});
			}
		},
	},
	
	computed: {

	},
	directives: {

	},
	created() {


	}
}
</script>

<style scoped>


</style>