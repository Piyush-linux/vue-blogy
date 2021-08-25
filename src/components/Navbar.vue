<template>
    <section class="NAV">
        <nav class="navbar" role="navigation" aria-label="main navigation" style="border-radius: 0;">
            <!-- logo -->
            <div class="navbar-brand">
                <a class="navbar-item" href="/">
                    <!-- <img src="https://image.flaticon.com/icons/png/512/5393/5393225.png"> -->
                    <span class="icon is-medium has-text-white">
                        <span class="iconify" data-icon="cil:pen"></span>
                    </span>
                </a>
                <!-- toggler -->
                <a role="button" class="navbar-burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
                    <span aria-hidden="true"></span>
                    <span aria-hidden="true"></span>
                    <span aria-hidden="true"></span>
                </a>
            </div>
            <!-- menu -->
            <div id="navbarBasicExample" class="navbar-menu">
                <div class="navbar-end">
                    <a class="navbar-item">
                        <div class="field">
                            <span class="control">
                                <input type="text" class="input" placeholder="S E A R C H">
                            </span>
                        </div>
                    </a>
                    <div class="navbar-item">
                            <div class="button is-light is-outlined" @click="createBlog('createModal')">
                                C R E A T E
                        </div>
                    </div>
                </div>
            </div>
        </nav>
    </section>
</template>
<script>
export default {
    name: 'Navbar',
    methods:{
        createBlog(mdl){
            this.$emit('emitCreateBlog',mdl)
        }
    }
    // props: {
    //   msg: String
    // }
}
</script>
<style>
</style>