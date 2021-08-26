<template>
    <section class="NAV">
        <nav class="navbar" role="navigation" aria-label="main navigation" style="border-radius: 0;">
            <!-- logo -->
            <div class="navbar-brand">
                <a class="navbar-item" href="/">
                    <!-- <img src="https://image.flaticon.com/icons/png/512/5393/5393225.png"> -->
                        <span class="icon is-large has-text-white">
                            <span class="iconify" data-icon="jam:pen-f"></span>
                        </span>
                        <span class="title has-text-white f1">BLOGY</span>
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
                                <input type="text" class="input" placeholder="S E A R C H" v-model="search" @input="searchBlog">
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
    // props:["logo"],
    data(){
        return{
            search:''
        }
    },
    methods:{
        createBlog(mdl){
            this.$emit('emitCreateBlog',mdl)
        },
        searchBlog(){
            this.$emit('emitSearch',this.search)
        }
    }
    // props: {
    //   msg: String
    // }
}
</script>
<style>
</style>