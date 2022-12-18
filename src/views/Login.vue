<template>
    <div style="background-color: grey;">
        <Header />



        <div class="card position-absolute translate-middle shadow-lg p-4  "
            style=" display: block; width: 40rem; height: 22rem; color: black; left:50%; top:45%; border-radius: 10px;">
            <div class="position.position-relative start-0 top-50 text-center fs-4"> Login</div>
            <form @submit.prevent="login">
                <div class="form-floating mb-2 mx-auto" style="width: 85%; margin: 1.5rem;">
                    <input v-model="user.email" name="email" type="email" class="form-control"
                        id="exampleFormControlInput1" placeholder="Email address" style="border-radius:9px;">
                    <label for="exampleFormControlInput1">Email address</label>
                </div>
                <div class="form-floating mb-3 mx-auto" style="width: 85%; margin: 1.5rem;">
                    <input v-model="user.password" name="password" type="password" class="form-control"
                        id="floatingPassword" placeholder="Password" style="border-radius:9px;">
                    <label for="floatingPassword">Password</label>
                </div>
                <button class="position-absolute btn btn-dark translate-middle-x p-2"
                    style="left: 50%; font-size: 18px; color: #00FF00;" type="submit">Sign In</button>

            </form>
        </div>

        <Footer />

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
                email: '',
                password: '',
            },
            submitting: false,
        }
    },

    methods: {
        async login() {
            console.log(this.user);

            const canLogin = await this.$store.dispatch('user/loginUser', this.user);
            if (canLogin) {
                //console.log(this.$store.getters('user/getUser'));
                //this.$store.commit
                //console.log(this.$store.getters.loginUser);
                this.error = false;
                console.log(this.$store.getters['user/getUser']);
                this.$router.push({ path: '/message/5' });
            }
            else this.error = true;
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