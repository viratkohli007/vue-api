<template>
<div>
 <div>
 	  <form>
  <div class="form-group row">
    <label  class="col-sm-2 col-form-label col-form-label-sm">Latitude</label>
    <div class="col-sm-10">
      <input type="text" class="form-control form-control-sm" id="colFormLabelSm" v-model="lat">
    </div>
  </div>
  <div class="form-group row">
    <label class="col-lg-2 col-form-label">Longitude</label>
    <div class="col-sm-10">
      <input type="text" class="form-control" id="colFormLabel"  v-model="long">
    </div>
  </div>
  <div class="form-group row">
      <input type="button" class="btn btn-primary" id="colFormLabel" placeholder="Longitude" @click="getInfo()">
    </div>
</form>
<div>
	<pre>
   	{{info}}
  </pre>
   </div>

 </div>


</div>
</template>

<script>
	import axios from 'axios'
export default{
	data(){
		return{
     info: null,
     lat: null,
     long: null
		}
	},
	methods: {
		getInfo(){

       axios.get('https://api.darksky.net/forecast/723bef41e40f424d364f7ce3d61ffd70/'+this.lat+','+this.long)
      .then(response => (this.info = response)).catch(err=>{
      	console.log(err)
      })
		}
	}
}
</script>
