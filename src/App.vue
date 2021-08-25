<template>
    <!-- nav -->
    <Navbar  @emitCreateBlog="openModal"/>
    <!-- blog -->
    <Blog :blgs="blgs" @emitOpenBlog="openBlog" @emitDeleteBlog="deleteBlog" />
    <!-- modal -->
     <!-- computed:> Create  -->
     <!-- computed :>  modal -->
        <div class="modal" ref="blogModal">
            <div class="modal-background"></div>
            <div class="modal-content">
                <div class="box section">
                    <div class="content is-medium">
                        <h1 class="title">
                            {{ modal.title }}
                        </h1>
                        {{ modal.content }}
                    </div>
                </div>
            </div>
            <button class="modal-close is-large" aria-label="close" @click="closeModal('blogModal')"></button>
        </div>
     <!-- <Create /> -->
        <div class="modal" ref="createModal">
            <div class="modal-background"></div>
            <div class="modal-content">
                <div class="box section">
                  <!-- title -->
                    <div class="field">
                      <div class="control">
                        <input type="text" class="input is-medium is-info" placeholder="title">
                      </div>
                    </div>
                    <!-- content -->
                    <div class="field">
                      <div class="control">
                        <textarea class="textarea has-fixed-size is-medium is-info" rows="13" placeholder="Content..."></textarea>
                      </div>
                    </div>
                </div>
            </div>
            <button class="modal-close is-large" aria-label="close" @click="closeModal('createModal')"></button>
        </div>
    <!-- footer -->
</template>
<script>
// import HelloWorld from './components/HelloWorld.vue'
import Navbar from './components/Navbar.vue'
import Blog from './components/Blog.vue'
// import HelloWorld from './components/HelloWorld.vue'

export default {
    name: 'App',
    components: {
        Navbar,
        Blog
    },
    data(){
        return{
            id: 3,
            openView: 0,
            blgs:[
                { id: 0, title: "Cat", content: "tandard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.Why do we use it?It is a long established fact that a " },
                { id: 1, title: "Dog", content: "reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using 'Content here, content here', making it look like readable English. Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like)." }
            ]
        }
    },
    methods:{
        // createBlog(){

        // },
        openModal(mdl){
            let modal = this.$refs[mdl]
            modal.classList.add("is-active")
        },
        closeModal(mdl){ // close Modal > craete , viewBlog
            let modal = this.$refs[mdl]
            modal.classList.remove("is-active")
        },
         openBlog(id) {
            this.openView = id
            let modal = this.$refs["blogModal"]
            modal.classList.add("is-active")
            console.log(this.blgs[id])
        },
        deleteBlog(e) {
            this.blgs.map((ele, i) => {
                if (ele.id == e) {
                    this.blgs.splice(i, 1)
                    // console.log(i)
                    // delete this.blgs[i]
                }
            })
        },
    },
     computed: {
        modal() {
            let id = this.openView
            let blog = this.blgs[id]
            return blog
        }
    }
}
</script>
<style>
.iconify {
    font-size: 3rem;
}

.blg {
    border: 2px solid #74b9ff;
    /*border: 2px solid #fab1a0;*/
    border-radius: 20px;
    margin-top: 1rem;
}

.content .title {
    color: #34495e;
}
</style>
<!-- 
Componnet : get > store > use
 -->