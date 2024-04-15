<template>

    <div v-for="index in 3" key="index">
        <br>
    </div>
    <div class="container mb-3">
        <form action="">
            <div class="mb-3">
                <label for="page-title" class="form-label">
                    Page Title
                </label>
                <input 
                type="text" 
                class="form-control"
                :class = "resultForm"

                v-model="pageTitle"
                >
            </div>
            <div class="mb-3">
                <label for="content" class="form-label">
                    Content
                </label>
                <textarea
                    :class = "resultForm"
                    class="form-control" 
                    rows="5"
                    v-model="pageContent"
                ></textarea>
            </div>
            <div class="mb-3">
                <button 
                    class="btn btn-primary"
                    :disabled="isFormValid"
                    @click.prevent="submitForm"
                    
                >
                    Create Page
                </button>
            </div>
        </form>
    </div>
    
</template>
<script>
export default{
    props: ['pageCreated'],
    computed:{
        isFormValid(){
            return !this.pageTitle || !this.pageContent
        },
        resultForm(){
            return this.isFormValid? 'is-invalid' : 'is-valid'
        }
    },
    data(){
        return{
            pageTitle: '',
            pageContent: ''
        }
    },
    methods : {
        submitForm(){
            if(!this.pageTitle || !this.pageContent){
                alert("Por favor complete tudo")
                return
            }
            this.pageCreated({link:{url:this.pageTitle,text:this.pageTitle},
                pageTitle:this.pageTitle,
                pageContent: this.pageContent})
        }
    },
    watch: {
    pageTitle() {
    this.pageContent = `Isso é um teste ${this.page}`;
  }
}

}
</script>