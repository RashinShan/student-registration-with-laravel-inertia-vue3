<script setup>
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});

let hoverLogin = false;
let hoverRegister = false;








</script>

<template>
    <Head title="Welcome" />

    <div class="relative bg-danger p-4 text-center text-white">
        <h1 class="font-weight-bold h1 mb-3">Student Reg System</h1>
        
        <div v-if="canLogin" class="position-fixed top-0 end-0 p-6 text-end">
            <Link
                v-if="$page.props.auth.user"
                :href="route('dashboard')"
                class="font-weight-bold text-gray-600 text-decoration-none"
                >Dashboard</Link
            >

            <template v-else>
                <Link
                    :href="route('login')"
                    class="font-weight-bold text-gray-600 text-decoration-none"
                    :class="{ 'text-dark': !hoverLogin, 'text-primary': hoverLogin }"
                    @mouseover="hoverLogin = true"
                    @mouseleave="hoverLogin = false"
                >
                    Log in
                </Link>

                <Link
                    v-if="canRegister"
                    :href="route('register')"
                    class="ms-4 font-weight-bold text-gray-600 text-decoration-none"
                    :class="{ 'text-dark': !hoverRegister, 'text-primary': hoverRegister }"
                    @mouseover="hoverRegister = true"
                    @mouseleave="hoverRegister = false"
                >
                    Register
                </Link>
            </template>
        </div>
    </div>

   


    <div class="container mt-5">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Welcome to Student Registration System</div>
                    
                    <div class="card-body">
                        <p class="card-text">
                            This system allows you to manage student registrations efficiently.
                            You can easily add, edit, and delete student records.
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <footer class="footer mt-5">
        <div class="container">
            <span class="text-muted">© 2024 Student Registration System</span>
        </div>
    </footer>

</template>


<style>
.footer {
    position: fixed;
    bottom: 0;
    width: 100%;
    background-color: #f8f9fa;
    text-align: center;
    padding: 10px 0;
}


</style>
