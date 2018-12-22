
<template>
<div class="group">
     <div class="group-label">
         <label class="label-style">
             <input type="checkbox" :value="group.id" v-model="allSelectd"
             @change="groupChange()"><span class="text">group {{group.id}}</span>
         </label>
     </div>
    <div class="content-box">
            <label class="label-style" v-for="device in group.devices" :key="`device_${device.id}`">
             <input type="checkbox" :value="device.id" v-model="device.active" name="device" @change="change(device)"/>
             <span class="text">{{device.name}}</span>
          </label>
    </div>
</div>
</template>

<script>
import 'lodash'

export default {
    name:'devices-group',
    props:['group'],
    watch: {
        group:{
            handler: function(v)  {
                console.log('in watch group' , v);
            },deep: true
        }
  },
    computed:{
        allSelectd:{
            get: function () { 
                    if(this.group.devices.length === this.getcounter())
                        return true;
                    else  
                        return false;
            },
            set: function (newValue) {
                return newValue;
            },
        }
    },
    created(){
            this.group.devices.forEach(element => {
              if(element.active === 1){
                 this.$emit('pushDeviceToArray' , element);
              }
        });
    },
  
    methods:{
        getcounter(){
            let counter = 0;
               this.group.devices.forEach(element => {
                   if(element.active == 1){
                       counter++;
                   }
               });   
               return counter
        },
        change(device){
                if(device.active){
                     device.active = 1;
                         this.$emit('pushDeviceToArray' , device);
                
                }else{
                   device.active = 0;
                     this.$emit('removeDeviceFromArray' , device);
        
                }
        },
        groupChange(){
            console.log('groupChange' ,this.allSelectd);
            if(!this.allSelectd){
                this.group.devices.forEach(element => {
                       if( element.active )
                        return;

                    element.active = 1;
                     this.$emit('pushDeviceToArray' , element);
                });
             } else{
                this.group.devices.forEach(element => {
                            if( !element.active )
                                return;

                            element.active = 0;
                            this.$emit('removeDeviceFromArray' , element);
                    });
                }

        },
    }
};
</script>

<style lang="scss">
    .group-label{
        background:#2644b4fa;
        color: #fff;
        padding: 10px 0.5rem;
        padding-left: 15px;

    }
</style>

