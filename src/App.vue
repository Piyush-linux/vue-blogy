<template>
    <!-- nav -->
    <Navbar  @emitCreateBlog="openModal"  @emitSearch="searchBlog" />
    <!-- blog -->
    <Blog :blgs="blgs" @emitOpenBlog="openBlog" @emitDeleteBlog="deleteBlog" v-if="viewBlog"/>
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
                        <input type="text" class="input is-medium is-info" placeholder="title" v-model="inp_title">
                      </div>
                    </div>
                    <!-- content -->
                    <div class="field">
                      <div class="control">
                        <textarea class="textarea has-fixed-size is-medium is-info" rows="13" placeholder="Content..." v-model="inp_content"></textarea>
                      </div>
                    </div>
                    <!-- submit -->
                    <div class="field has-addons has-text-centered">
                        <div class="control ">
                            <div class="button is-danger " @click="clearBlog">
                                <span class="icon">
                                    <span class="iconify" data-icon="ic:outline-clear-all"></span>
                                </span>
                                <span>CLEAR</span>
                            </div>
                        </div>
                        <div class="control">
                            <div class="button is-success " @click="createBlog">
                                    <span> SUBMIT </span>
                                    <span class="icon">
                                        <span class="iconify" data-icon="bx:bxs-send"></span>
                                    </span>
                            </div>
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
            // logo:require('@/assets/logo.png'),
            inp_title:'',
            inp_content:'',
            id: 2,
            openView: 0,
            viewBlog:true,
            blgs:[
                { id: 0, title: "Cat", content: "tandard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.Why do we use it?It is a long established fact that a " },
                { id: 1, title: "Dog", content: "reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using 'Content here, content here', making it look like readable English. Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like)." }
            ]
        }
    },
    methods:{
        // notify(){
        // 
        // },
        searchBlog(ser){
            let qry = document.querySelectorAll(".blg")
            let search = ser.toLowerCase()
            qry.forEach((ele,i) =>{
                let title = ele.querySelector(".title").innerText.toLowerCase()
                // console.log(title.includes(search))
                if(title.includes(search)){
                    ele.style.display = "block"
                    // console.log(ele)
                }else{
                    ele.style.display = "none"
                    // console.log(ele)
                }
            });
            // console.log(`searching ... ${ ser }`)
            // console.log(qry)
        },
        createBlog(){
            if( this.inp_title.length <= 1 || this.inp_content.length <= 1 ){
                alert("plese input valid value")
            }else{
                let blg = {id: this.id , title: this.inp_title , content: this.inp_content}
                console.log(blg)
                this.blgs.push(blg)
                this.id++
                this.closeModal('createModal')
                this.inp_title=''
                this.inp_content=''
            }
        },
        clearBlog(){
            this.inp_title=''
            this.inp_content=''
        },
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
            if(this.blgs.length > 1){
                this.blgs.map((ele, i) => {
                    if (ele.id == e) {
                        this.blgs.splice(i, 1)
                    }
                })
            }else{
                this.viewBlog = false
            }
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
.f1{
    font-family: Balsamiq Sans;
}
.field.has-addons{
    justify-content: center;
}
.col{
    display: flex;
}
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