<script setup>
import { ref,computed  } from 'vue';


//variable drinking
const travelList=ref([
  {name: 'สุนทรารมณ์',  price:500, img:"https://scontent.fbkk13-2.fna.fbcdn.net/v/t39.30808-6/327442369_874305543617514_7552528986654738604_n.jpg?_nc_cat=110&ccb=1-7&_nc_sid=a2f6c7&_nc_eui2=AeFNdHIyDFw8l9dSHVOxGbtd2Q6BSD08VdDZDoFIPTxV0Jyx8MQf2dauMZCHSslW0V1nOlqKwTeXRF6hl0wVPuBq&_nc_ohc=QGIXLCcANAEAX8oL9of&_nc_ht=scontent.fbkk13-2.fna&oh=00_AfDGtzcszEljTAHl8QKGUijSrx-jt8GwLZ5OZs6OTu4VSQ&oe=64FD9D20", quantity: 0 }, 

  {name:'Overnight',  price:750, img:"https://scontent.fbkk13-2.fna.fbcdn.net/v/t39.30808-6/314943429_107842845474701_641691726405226769_n.jpg?stp=cp6_dst-jpg&_nc_cat=107&ccb=1-7&_nc_sid=a2f6c7&_nc_eui2=AeFloVqAmAQK63gBmvRlILSFEYxzLzXtdwsRjHMvNe13C67jqz5C4ozZtnfeVB-bdVvF2m0RlI6vAA4gmgVza1hd&_nc_ohc=JsU_-083hU4AX9u2vHL&_nc_ht=scontent.fbkk13-2.fna&oh=00_AfDn433NRDpL4MAAkFVmrpWijqDVhNrFYXkfdIiOmAr2pw&oe=64FDD6B1", quantity: 0 },
  
  {name:'Tamma',      price:1500, img:"https://scontent.fbkk13-2.fna.fbcdn.net/v/t39.30808-6/361305041_779199773993037_7111305937619716444_n.jpg?_nc_cat=110&ccb=1-7&_nc_sid=a2f6c7&_nc_eui2=AeGZ36SZ7tHE4Sn56ahHG-4VKhovrXyAa8YqGi-tfIBrxqe1tPcilruoK6M8iPurXs2EtvRAUFDpW4HyLULu-tZG&_nc_ohc=NUl9gU8b32gAX_PJpz-&_nc_ht=scontent.fbkk13-2.fna&oh=00_AfA2l1ggQGMrfsjdgRgq6o2Vr20QfaEeiIvMAwIHJ_KcXQ&oe=64FF0047", quantity: 0 },

  {name:'ไปยาล',     price:1599, img:"https://scontent.fbkk13-2.fna.fbcdn.net/v/t39.30808-1/326435697_501993212005268_2267045348590722770_n.jpg?stp=dst-jpg_p320x320&_nc_cat=103&ccb=1-7&_nc_sid=754033&_nc_eui2=AeGmFPzsMIq3BFoj1PViby3YxTbvRg4F5HPFNu9GDgXkc_ntcZ1iiswsTq9-jcH-pP3KvXD7sj7D6hgpksqlR7X8&_nc_ohc=w70TqL0LBHMAX9eRmtz&_nc_ht=scontent.fbkk13-2.fna&oh=00_AfDtcL42wBIGzSJBRdL2HOvzWz8Iouxb-CLNFaSsdyGKeQ&oe=64FDEFC9", quantity: 0 },

  {name:'Too nice',    price:1699, img:"https://scontent.fbkk13-2.fna.fbcdn.net/v/t39.30808-6/292496235_1007767096737663_225747972753273688_n.png?_nc_cat=110&ccb=1-7&_nc_sid=a2f6c7&_nc_eui2=AeElcXBRemzlCc00lIr4Gg4HzTWRn5lngH3NNZGfmWeAfdM0r7nLsyIZaexMz8_UB8jL6tg2M4vxxRmT3iKLZbmm&_nc_ohc=R0AqwtXy2XQAX-6usnI&_nc_ht=scontent.fbkk13-2.fna&oh=00_AfCKCH-GD6spsF2crGqpoQLClRFzW_2zxeLiQdyhl16SXQ&oe=64FDB576", quantity: 0 },


  {name:'ท่าช้าง',  price:1890,  img:"https://scontent.fbkk13-2.fna.fbcdn.net/v/t39.30808-6/350942472_940270750565444_6986476706008406745_n.jpg?_nc_cat=104&ccb=1-7&_nc_sid=a2f6c7&_nc_eui2=AeGOw7uk2VFH7K0Y1VV60YyZJnOKgtUtkswmc4qC1S2SzHt3w5MKrvNCf6Jeuix0rENdMiRxxWccKJITy2tbgpFm&_nc_ohc=EBl4NSGR99UAX9T9gPf&_nc_ht=scontent.fbkk13-2.fna&oh=00_AfCxWFHC52mx2q6QlRYlCfWtamuHpgvz2Rl7wsWrb3JeQw&oe=64FE7920", quantity: 0 },


  {name:'Beer lab',      price:675, img:"https://scontent.fbkk13-2.fna.fbcdn.net/v/t39.30808-6/326776461_983306725977390_1286925122631726978_n.jpg?_nc_cat=111&ccb=1-7&_nc_sid=a2f6c7&_nc_eui2=AeF1Ywb4j0jzAKiBj2OSSgPDDbJxNGoeGtoNsnE0ah4a2rGXYUI_AKkz9jMg_OiM6XP4-mQuh4pgkXOJfXGs7H2T&_nc_ohc=C2NpKwZz5ZcAX-iRwGx&_nc_ht=scontent.fbkk13-2.fna&oh=00_AfCGwZMuYRbBc1i9Ivz1WNNLf6IBiCJgzMhZd5ZieomqYQ&oe=64FE3E79", quantity: 0 },


  {name:'Warm up',     price:1250, img:"https://scontent.fbkk13-2.fna.fbcdn.net/v/t39.30808-6/326148970_1521569305000988_2338094468162899732_n.jpg?_nc_cat=111&ccb=1-7&_nc_sid=a2f6c7&_nc_aid=0&_nc_eui2=AeHdrRzQLjAXk3z9zYSatohZJSB-z1el8TIlIH7PV6XxMsYI3VPYXaWft8sKQRkEMdnn378aOgRBez-gwkIXATgA&_nc_ohc=-nloMFue0PQAX-oPt_-&_nc_ht=scontent.fbkk13-2.fna&oh=00_AfBXrWHaV-03hPUW252v3dkcfrL-3dEN5uWBqRGG3hOVzw&oe=64FF1E18", quantity: 0 },
])


//เก็บ list การจอง 
const list_local = ref([


]);


//function
function list_local_control(name, quantity) {
  const existingItemIndex = list_local.value.findIndex(item => item.name === name);

  if (existingItemIndex !== -1) {
    list_local.value[existingItemIndex].quantity += quantity;
    list_local.value[existingItemIndex].price = list_local.value[existingItemIndex].quantity * travelList.value.find(item => item.name === name).price;
  } else {
    const item = {
      name: name,
      quantity: quantity,
      price: quantity * travelList.value.find(item => item.name === name).price
    };
    list_local.value.push(item);
  }
}


function incrementQuantity(item) {
  item.quantity++;
  item.price = item.quantity * travelList.value.find((travel) => travel.name === item.name).price;
}

function decrementQuantity(item) {
  if (item.quantity > 0) {
    item.quantity--;
    item.price = item.quantity * travelList.value.find((travel) => travel.name === item.name).price;
  }
}

function removeItem(index) {
  list_local.value.splice(index, 1);
}



//pop up

const form_costumer = ref({
  name: "",
  phone: "",
  date: "",
  time: ""
});

const showPopup = ref(false);

const totalCost = computed(() => {
    return list_local.value.reduce((acc, item) => acc + item.price, 0);
});

function displayPopup() {
    showPopup.value = true;
}

function togglePopup() {
  showPopup.value = !showPopup.value;
}


</script>



<template>

  <HelloWorld v-if="showPopup" />
  <div class="overlay" v-if="showPopup">
    <HelloWorld />
  </div>

  <div class="header">
    <H1>รายการสินค้า</H1>
  </div><hr>


  <div class="container text-center">
    <div class="row">
      <div class="col" v-for="(i,index) in travelList" :key="index">
        <div class="card" style="width: 18rem;" >
          <img :src="i.img" class="card-img-top">
          <div class="card-body">
            <h3 class="card-title">{{ i.name }}</h3>
            <p>ราคาโต๊ะ : {{i.price}}</p>
            <h6>***จำกัด 5 คนต่อ 1 โต๊ะ***</h6>
            <p class="card-text">จำนวนโต๊ะ 
               <input type="number" class="cout_value " v-model="i.quantity">
            </p>
            <a class="btn btn-primary" @click="list_local_control(i.name, i.quantity)"> จองโต๊ะ </a>
          </div>
        </div>
      </div>
    </div>
  </div> 

 

  <h1 style="text-align: center; " v-if="list_local.length>0" class="header">รายการจองโต๊ะ</h1>
  <div class="list_cout text-center">
    <table class="table table-hover" v-if="list_local.length>0">
      <table class="table">
        <thead>
          <tr>
            <th scope="col">ลำดับ</th>
            <th scope="col">ชื่อร้าน</th>
            <th scope="col">จำนวนโต๊ะ</th>
            <th scope="col">ราคา</th>
            <th scope="col"></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(i,index) in list_local" :key="index" >
            <th scope="row">{{index+1}}</th>
            <td>{{ i.name }}</td>
            <td>
              <div class="quantity-controls">
                <button type="button" class="btn btn-danger"   @click="decrementQuantity(i)" :disabled="i.quantity === 0"> - </button>
                <span>{{ i.quantity }}</span>
                <button type="button" class="btn btn-success" @click="incrementQuantity(i)">+</button>
              </div>
            </td>
            <td>{{ i.price}}</td>
            <td>
              <button type="button" class="btn btn-danger" @click="removeItem(index)" >ลบรายการ</button>
            </td>
          </tr>
        </tbody>
      </table>  
    </table>
  </div>  

  
  <div class="contrainer_costumer " v-if="list_local.length>0">
  <div class="form_box"> <h2 style="text-align: center;">กรุณากรอกข้อมูล</h2></div>
  <form>
    <div class="form_box">
      <label for="name">ชื่อ-นามสกุล </label><br>
      <input type="text" id="name" class="form-control" v-model="form_costumer.name" required>
    </div>
    <div class="form_box">
      <label for="phone">เบอร์โทร </label><br>
      <input type="tel" id="phone" class="form-control" v-model="form_costumer.phone" required>
    </div>
    <div class="form_box">
      <label for="date">วันที่ </label><br>
      <input type="date" id="date" class="form-control" v-model="form_costumer.date" required>
    </div>
    <div class="form_box">
      <label for="time">เวลา </label><br>
      <input type="time" id="time" class="form-control" v-model="form_costumer.time" required>
    </div>
    <div class="form_box">
      <button type="button" class="btn btn-success" @click="togglePopup"> ยืนยันการจอง </button>
    </div>
  </form>
</div>


<div v-if="showPopup" class="overlay">

  <div class="popup">
      <h2 style="text-align: center; color:green ;">ยืนยันการจองสำเร็จ</h2>
      <h3 >รายละเอียด</h3>
      <p><strong>ชื่อ-นามสกุล:</strong> {{ form_costumer.name }}</p>
      <p><strong>เบอร์โทร:</strong> {{ form_costumer.phone }}</p>
      <p><strong>วันที่:</strong> {{ form_costumer.date }}</p>
      <p><strong>เวลา:</strong> {{ form_costumer.time }}</p>
      
      <table class="box_table">
          <thead>
              <tr>
                  <th>ลำดับ</th>
                  <th>ชื่อร้าน</th>
                  <th>จำนวนโต๊ะ</th>
                  <th>ราคา</th>
              </tr>
          </thead>
          <tbody>
              <tr v-for="(i, index) in list_local" :key="index">
                  <td>{{ index + 1 }}</td>
                  <td>{{ i.name }}</td>
                  <td>{{ i.quantity }}</td>
                  <td>{{ i.price }}  บาท </td>
              </tr>
          </tbody>
      </table>

      <p><strong>รวม:</strong> {{ totalCost }} บาท</p>

      <button class="btn btn-danger" @click="showPopup = false">ปิดหน้าต่าง</button>
  </div>
</div>



</template>


<style>
*{
  padding: 5px;
}
.header{
  text-align: center;
}
.card-img-top{
  height: 100%;
  padding: 25px;
}

.col{
  padding: 10px;
}


.contrainer_customer {
  justify-content: center;
  align-items: center;
  margin-left: 20%;
  margin-right: 20%;

}

.form_box{
    justify-content: center;
    align-items: center;
    padding: 5px;
    margin-left: 30%;
    margin-right: 30%;
}


.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
}


.popup {
  background-color: #fff;
  padding: 20px;
  border-radius: 10px;
  width: 70%;
  max-height: 80%;
  overflow-y: auto;
}

.header{
  padding: 25px;
}

</style>