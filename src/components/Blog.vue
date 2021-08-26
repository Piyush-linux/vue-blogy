<template>
    <section class="Blog section">
        <div class="container">
            <div class="columns is-multiline">
                <!-- blg1 -->
                <div class="column is-full blg" v-for="blg in blgs" :id="blg.id" v-if="blgs.length >= 1">
                    <!-- blg_con_1 -->
                    <div class="columns">
                        <div class="column is-10">
                            <div class="content is-medium has-text-grey">
                                <h1 class="title mb-0"> {{ blg.title }} </h1>
                                {{ blg.content.slice(0,100) }} ...
                            </div>
                        </div>
                        <div class="column">
                            <div class="field ">
                                <div class="control has-text-right">
                                    <button class="button is-rounded is-danger is-outlined" @click="deleteBlog(blg.id)">
                                        <span class="icon">
                                            <span class="iconify" data-icon="ant-design:delete-outlined"></span>
                                        </span>
                                    </button>
                                </div>
                            </div>
                            <div class="field ">
                                <div class="control has-text-right">
                                    <button class="button is-rounded is-success is-outlined" @click="openBlog(blg.id)">
                                        <span class="icon">
                                            <span class="iconify" data-icon="fluent:arrow-expand-24-filled"></span>
                                        </span>
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
       
    </section>
</template>
<script>
export default {
    name: 'Blog',
    props:["blgs"],
    // data() {
    //     return {
            
    //     }
    // },
    methods: {
        // del,open
        openBlog(id) {
            this.$emit('emitOpenBlog',id)
        },
        deleteBlog(e) {
          this.$emit('emitDeleteBlog',e) 
          console.log(e) 
        },
    },
   
    // props: {
    //   msg: String
    // }
}
</script>
<style>
.title {
    margin-bottom: 0;
}
</style>