<template>
  <div class="modal fade text-white" :id="`productEdit`+product.prodId" tabindex="-1" :aria-labelledby="`productEditLabel`+product.prodId" aria-hidden="true">
    <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
            <div class="modal-header">
                <h5 style="color:greenyellow;" class="fw-bold modal-title">Editing - {{product.prodName}}</h5>
                <button type="button" :id="`productClose`+product.prodId" class="btn-close btn-close-white" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <div class="modal-body p-5">
                <form class="row" @submit="editProduct">
                    <div class="col-md-6 my-4">
                        <label class="w-100">Name</label>
                        <input class="w-100" v-model="product.prodName" type="text">
                    </div>
                    <div class="col-md-6 my-4">
                        <label class="w-100">Category</label>
                        <select class="w-100" v-model="product.category">
                            <option selected value="Accessory">Accessory</option>
                            <option value="Console">Console</option>
                            <option value="Computer Part">Computer Part</option>
                            <option value="Computer Accessory">Computer Accessory</option>
                        </select>
                    </div>
                    <div class="col-md-6 my-4">
                        <label class="w-100">Quantity</label>
                        <input class="w-100" v-model="product.quantity" type="number">
                    </div>
                    <div class="col-md-6 my-4">
                        <label class="w-100">Price</label>
                        <input class="w-100" v-model="product.price" type="number">
                    </div>
                    <div class="col-md-12 my-4">
                        <label class="w-100">Image Link</label>
                        <textarea style="resize:none" cols="30" rows="3" v-model="product.prodImg" class="w-100" type="text"></textarea>
                    </div>
                    <div class="col-md-12 my-4">
                        <label class="w-100">Description</label>
                        <textarea style="resize:none;" v-model="product.prodDescription" class="w-100" type="text" ></textarea>
                    </div>
                    <button type="submit" class="button">Submit</button>
                </form>
            </div>
            <div class="modal-footer">
                <button class="button me-auto" data-bs-dismiss="modal">Cancel</button>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    props:['product'],
    methods:{
        editProduct(e){
            e.preventDefault();
            const newProduct = {
                prodId: this.product.prodId,
                prodName: this.product.prodName,
                prodImg: this.product.prodImg,
                prodDescription: this.product.prodDescription,
                category: this.product.category,
                quantity: this.product.quantity,
                price: this.product.price
            }
            document.getElementById(`productClose${this.product.prodId}`).click();
            this.$store.dispatch('editProduct', newProduct);
        }
    }
}
</script>

<style scoped>

.modal{
    --bs-modal-width:800px !important;
}

label{
    text-align: left;
    padding-left:8px;
    color:greenyellow;
    font-weight: 900;
}

select{
    background: transparent;
    border:2px solid #757575;
    color: white;
    height: 42px;
}

option{
    background:#0c0c0c;
}

</style>