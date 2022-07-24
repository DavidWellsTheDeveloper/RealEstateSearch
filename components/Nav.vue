<template>
            <b-navbar toggleable="lg" type="dark" variant="dark">
                <b-navbar-brand href="#">Real Estate Search</b-navbar-brand>

                <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

                <b-collapse id="nav-collapse" is-nav>
                <b-navbar-nav>
                    <b-nav-item href="#">Link</b-nav-item>
                    <b-nav-item href="#" disabled>Disabled</b-nav-item>
                </b-navbar-nav>

                <!-- Right aligned nav items -->
                <b-navbar-nav class="ml-auto">
                    <b-nav-item>Something</b-nav-item>
                </b-navbar-nav>
                </b-collapse>
            </b-navbar>
</template>

<script>
    export default {
        data() {
            return {
                pages: [
                    { name: 'Home', path: '/' }
                ]
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>