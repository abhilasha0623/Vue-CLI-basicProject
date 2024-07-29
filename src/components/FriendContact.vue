<template>
  <li>
    <h2>{{ name }}{{ isFavourite ==='1'?'(Favourite)' : '' }}</h2>
     <button @click="toggleFavourite">Toggle Favourite</button>
    <button @click="toggleDetails">{{ detailsAreVisible?'Hide' : 'Show'}} Details</button>
 
  <ul v-if="detailsAreVisible">
    <li><strong>Phone:</strong>{{ phoneNumber }} </li>
    <li><strong>Email:</strong>{{ email }}</li>
  </ul>
  </li>
</template>

<script>
export default {
  // props:['name','phoneNumber','email','isFavourite'],
    props:{
      id:{
        type:String,
        required:true,
      },
      name:{
        type:String,
        required:true
      },
      phoneNumber:{
        type:String,
        required:true
      },
       emailAddress:{
        type:String,
        required:true
      },
       isFavourite:{
        type:Boolean,
        required:false,
        default:false,
        // validator:function(value){
        // return value === '1' || value === '0';
        // }

      },
    },

 data () {
    return {
      detailsAreVisible:false,
      // friend: {
      //  id:"manuel",
      //  name:"Manuel Louentx",
      //  phone:"12345 87654 908",
      //  email:"manuel@localhost.com",
      // },
      // friendIsFavourite:this.isFavourite
    }
 },
  methods: {
  toggleDetails() {
       this.detailsAreVisible=! this.detailsAreVisible;
  },
  toggleFavourite() {
        this.$emit('toggle-favourite',this.id)
  }
}
}
</script>