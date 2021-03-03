<template >
<div >
    <b-card >
    <h1 class="h1" >ข้อมูลรูปภาพสี</h1>
         
     <b-button variant="outline-primary" @click="loadUser">แสดงข้อมูลรูปภาพ</b-button>
     </b-card><br> 
     <div align="center"> 
    <b-row cols-lg="3" cols-md="3" cols-sm="1">
    <b-card 
    bg-variant=""  v-for="photos in photoList" :key="photos.id"
    img-src=""
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 200rem;"
    class="card " >
    
    <h1>album {{photos.albumId}}</h1>
      <b-row class="container">
      <b-col md="8" lg="8" sm="7">
      <b-card-text>
       <h3 align="left"> {{photos.id}}</h3> 
        <br> 
       <h5 align="left">  {{photos.title}}  </h5>  
       </b-card-text>
       </b-col>
       <b-col>
       <img :src="photos.thumbnailUrl" alt="" sizes="150px" srcset="">
       </b-col>
      </b-row> 
        <a :href="photos.url">ภาพขนาด 600x600</a>
    </b-card>
    </b-row>   
    </div> 
    </div>
 
</template>

<script>
import axios from"axios"; 
export default {
    data(){
        return{
        photoList:null,
         url:"http://jsonplaceholder.typicode.com/photos"
        };
    },
     methods:{
        loadUser(){
            axios.get(this.url)
            .then( response=>{ this.photoList = response.data;
            } )
            .catch(err => { console.log(err) } )
        },
     }
};
</script>
 <style>
.h1{
    color:#376ab8;
}
.h2{
   color: rgb(231, 238, 235);
   width: 12;
   font: 1em sans-serif;
}
.card{
    color: rgb(0, 0, 0);
}
.blackground{
    color: black;
}
</style>