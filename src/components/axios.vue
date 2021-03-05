<template >
<div class="app" >
    <body background="https://f.ptcdn.info/912/014/000/1390700865-02-o.jpg">
    <b-row>
    <b-col cols="md-sm-lg-2">
     <img src="https://markpeak.net/wp-content/uploads/2020/08/nasa-two-logos-700x394.png" 
     width="300" height="200"
     ></b-col>
     <b-col align-self="center">
    <h1 class="h1" >ข้อมูลการช็อกระหว่างดาวเคราะห์ (IPS)</h1>
     <b-button variant="light" @click="loadUser">แสดงข้อมูล</b-button>
     </b-col></b-row>
     <br>
     <div class="container">
    <b-row cols-lg="1" cols-md="1" cols-sm="1">
    <b-card class="ms-1"
         border-variant="primary"
        header="ข้อมูล"
        header-bg-variant="primary"
        header-text-variant="white"
        v-for="(data,index) in dataList" :key="index"
        tag="article"
        style="max-width: 200rem;" >
    
        <h1 align="center"> {{data.catalog}}</h1>
        <b-card-text >
        <h3 > ID กิจกรรม : {{data.activityID}}</h3> 
        <br>
        <b-row class="">
    <b-col col lg="3"><h3>โลเคชั่น : {{data.location}}</h3></b-col>
    <b-col cols="2" md="auto"></b-col>
    <b-col col lg="4"> <h3>เวลา : {{data.eventTime}}</h3></b-col>
    </b-row>
        <div v-for="i in data.instruments" :key="i">
          ชื่อ : {{i.displayName}}
        </div >
       </b-card-text>
        <a :href="data.link" target="_blank">ข้อมูลเพิ่มเติม</a>
   </b-card>
    </b-row>    
    </div>
    </body>
    </div>

</template>

<script>
import axios from"axios"; 
export default {
    data(){
        return{
        dataList:null,
         url:"https://api.nasa.gov/DONKI/IPS?startDate=2016-01-01&endDate=2016-01-30&api_key=DEMO_KEY"
        };
    },
     methods:{
        loadUser(){
            axios.get(this.url)
            .then( response=>{ this.dataList = response.data;
            } )
            .catch(err => { console.log(err) } )
        },
     }
};
</script>
 <style>
 #app{
    background-image:src="https://images.hdqwalls.com/wallpapers/moon-photography-by-nasa-5k-0w.jpg";
}
.h1{
        color:#fdfdfd;

}
.h2{
   color: rgb(231, 238, 235);
   width: 12;
   font: 1em sans-serif;
}
.ms-1 {
  margin-bottom:25px !important;

}

</style>