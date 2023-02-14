<template>
  <header>
    <the-header @handle-up-or-down-amount-cart="handleUpOrDownAmount"
     @handle-remove-cart = "handleRemove" :cartList="cartList"/>
     

  </header>
  <body>
    <the-productsList :productList="productList" :handleAddCart="handleAddCart" />
  </body>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import TheProductsList from "./components/TheProductsList.vue";
import sp1 from "./assets/sp1.webp";
import sp2 from "./assets/sp2.webp";
import sp3 from "./assets/sp3.webp";
import sp4 from "./assets/sp4.webp";
import sp5 from "./assets/sp5.webp";
import sp6 from "./assets/sp6.webp";
import sp7 from "./assets/sp7.webp";
import sp8 from "./assets/sp8.webp";
export default {
  name: 'App',
  components: {
    TheHeader,
    TheProductsList
  },
  data() {
    return {
      productList: [
        {
          id: 1,
          name: "Bộ Bàn Phím",
          image: sp1,
          description:
            "Phím và chuột có dây dài Phù hợp với nhiều loại hệ điều hành khác nhau, nhiều cấu hình máy của PC hoặc laptop. Đèn Led bắt mắt, phù hợp cho các game thủ chơi Game vào ban đêm Phím giả cơ nghe âm thanh rất thanh và êm Chuột Chuyên Game được thiết kế riêng dành cho game thủ và phòng net",
          price: 134000,
          sale: 10 / 100,
          quantityInStock: 10,
        },
        {
          id: 2,
          name: "Chuột Captain Marvel ",
          image: sp2,
          description:
            "Phím và chuột có dây dài Phù hợp với nhiều loại hệ điều hành khác nhau, nhiều cấu hình máy của PC hoặc laptop. Đèn Led bắt mắt, phù hợp cho các game thủ chơi Game vào ban đêm Phím giả cơ nghe âm thanh rất thanh và êm Chuột Chuyên Game được thiết kế riêng dành cho game thủ và phòng net",
          price: 250000,
          sale: 5 / 100,
          quantityInStock: 15,
        },
        {
          id: 3,
          name: "Laptop Gaming",
          image: sp3,
          description:
            "Phím và chuột có dây dài Phù hợp với nhiều loại hệ điều hành khác nhau, nhiều cấu hình máy của PC hoặc laptop. Đèn Led bắt mắt, phù hợp cho các game thủ chơi Game vào ban đêm Phím giả cơ nghe âm thanh rất thanh và êm Chuột Chuyên Game được thiết kế riêng dành cho game thủ và phòng net",
          price: 10500000,
          sale: 0 / 100,
          quantityInStock: 5,
        },
        {
          id: 4,
          name: "Lót Chuột",
          image: sp4,
          description: "lót chuột chống chày sước bàn ghế",
          price: 230000,
          sale: 5 / 100,
          quantityInStock: 35,
        },
        {
          id: 5,
          name: "Tai Nghe",
          image: sp5,
          description: "Tai Nghe hiện đại",
          price: 1000000,
          sale: 10 / 100,
          quantityInStock: 10,
        },
        {
          id: 6,
          name: "Loa Sony",
          image: sp6,
          description: "Nghe Nhạc cực chất",
          price: 750000,
          sale: 5 / 100,
          quantityInStock: 15,
        },
        {
          id: 7,
          name: "Màn Hình View Sonic",
          image: sp7,
          description: "Độ Phân Giải cực nét full HD không che",
          price: 134000,
          sale: 10 / 100,
          quantityInStock: 10,
        },
        {
          id: 8,
          name: "Mic Thu âm",
          image: sp8,
          description: "Khử Ổn Siêu Hiệu Quả",
          price: 300000,
          sale: 0 / 100,
          quantityInStock: 7,
        },
      ],
      cartList: [],
    };
  },
  methods: {
    handleAddCart(item){
const index = this.cartList.findIndex(
  cart => cart.id === item.id
  
);

    if(index !==-1) {
this.cartList[index].amount +=1
    } else {
      const newItem = {...item, amount:1}
      this.cartList = [...this.cartList, newItem]    }
  },
  handleRemove(cart){
    console.log("delete",cart)

this.cartList = this.cartList.filter((cartItem)=> cartItem.id !== cart.id)  
},
handleUpOrDownAmount(params){
const {cart,status} = params
const index = this.cartList.findIndex(
  cartItem => cart.id === cartItem .id  
);

if(index !== -1) {
  if(    this.cartList[index].amount < this.cartList[index].quantityInStock
){
  this.cartList[index].amount +=1
  } else {
    alert("khong dc tang nua")
  }
}
  if(status){
cart.amount +=1
  console.log("tangc",cart)
}else {
  if(this.cartList[index].amount > 1){
    this.cartList[index].amount -=1
  } else {
    alert("khong dc giamr nua")
  }

}
}
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
