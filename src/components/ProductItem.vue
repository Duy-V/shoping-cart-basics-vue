<template>
    <div class="card" style="width: 18rem;">
      <img class="card-img-top" :src="productItem.image" alt="Card image cap" />
      <div class="card-body">
        <h5 class="card-title">{{ productItem.name }}</h5>
        <div class="card-text text-danger">
          <h4 class="">{{ productItem.price }} VNĐ</h4>
        </div>
        <button class="btn btn-danger" @click="handleAddCart(productItem)">
          Mua
        </button>
        <button class="btn btn-info ml-2" @click="handleOpenModal">
          Chi Tiết
        </button>
      </div>
      
    </div>
 
<app-modal :isOpen="isOpenModal" :onClose="handleCloseModal">
        <product-detail :productItem="productItem"></product-detail>
      </app-modal>


  </template>
  
  <script>
import AppModal from './AppModal.vue'
import ProductDetail from './ProductDetail.vue';
  export default {
    data(){
      return {
        isOpenModal: false
      }
    },
    components: {
        AppModal,
        ProductDetail
  
    },
    props: {
        productItem: {
      type: Object,
    },
    handleAddCart: {
      type: Function,
    },
    },
   
    methods: {
       
        handleOpenModal(){
this.isOpenModal = true
console.log('open',this.isOpenModal)
        },
        handleCloseModal(){
this.isOpenModal = false

        }
    }
  }
  </script>
  
  <style></style>
  