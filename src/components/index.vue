<template>
  <div class="index">
      <form @submit.prevent="sendForm">
      <div class="all-box">
        <div class="box-wrap" >
            <div class="inner-box-wrap">
            <h3 class="box-title">1. Select blackboxes</h3>
            <devices-group  @pushDeviceToArray = "pushDeviceToArray" @removeDeviceFromArray ="removeDeviceFromArray" v-for="group in data.device_groups" :group="group" :key="`group${group.id}`"></devices-group>
        </div>
         </div>
        <div class="box-wrap">
             <div class="inner-box-wrap">
              <h3 class="box-title">2. Select protocols</h3>
               <div class="content-box">
            <label class="label-style" v-for="protocol in data.protocols" :key="`protocol${protocol.id}`">
                <input  type="checkbox" :value="protocol"
                v-model="cart.selectedProtocols" name="protocol"/>
                <span class="text"> {{protocol.name}}</span>
            </label>
           </div>
             </div>
         </div>
        <div class="box-wrap">
             <div class="inner-box-wrap">
              <h3 class="box-title">3. Select time period</h3>
                <div class="content-box"> 
                    <label class="label-style" v-for="time in data.times" :key="`times_${time.id}`">
                        <input  type="radio" :value="time" name="time" 
                         v-model="cart.selectedTime" />
                        <span class="text"> {{time.name}}</span>
                    </label>
                 </div>
             </div>
        </div>
        <div class="cart box-wrap">
             <div class="inner-box-wrap">
              <h3 class="box-title">4. Summary</h3>
                <div class="content-box">
                    <ul class="section" v-for="(category, index ) in cart"  
                     :key="`category${index}`">
                        <h4 class="cart-title"> {{index}} </h4>
                        <li v-if="index === 'selectedTime'" >{{category.name}}</li>
                       <li v-else v-for="item in category" :key="item.name">{{item.name}}</li>
                    </ul>
                </div>
         <div class="btns">
             <a href="javascript:;" class="btn" @click="clearAll">Clear</a>
             <button type="submit" class="btn">Start learning</button>
         </div>
         </div>
        </div>
     </div>
      </form>
  </div>
</template>




<script>
import { mapGetters, mapState } from 'vuex'
import DevicesGroup from './devicesGroup'
import axios from "axios";

export default {
  name: 'Index',
  components:{
      DevicesGroup,
  },
  data() {
    return {
        cart:{
            selectedDevices:[],
            selectedProtocols:[],
            selectedTime:[],  
        },
     data: {
            "device_groups": [{
            "id": "1",
            "name": "group 1",
            "devices": [{
                "id": 11,
                "name": "device 11",
                "active": 1
            }, {
                "id": 12,
                "name": "device 12",
                "active": 0
            }, {
                "id": 13,
                "name": "device 13",
                "active": 1
            }, {
                "id": 14,
                "name": "device 14",
                "active": 0
            }, {
                "id": 15,
                "name": "device 15",
                "active": 0
            }, {
                "id": 16,
                "name": "device 16",
                "active": 1
            }, {
                "id": 17,
                "name": "device 17",
                "active": 1
            }]
        
            }, {
            "id": "2",
            "name": "group 2",
            "devices": [{
                "id": 21,
                "name": "device 21",
                "active": 1
            }, {
                "id": 22,
                "name": "device 22",
                "active": 0
            }, {
                "id": 23,
                "name": "device 23",
                "active": 1
            }, {
                "id": 24,
                "name": "device 24",
                "active": 0
            }, {
                "id": 25,
                "name": "device 25",
                "active": 0
            }, {
                "id": 26,
                "name": "device 26",
                "active": 1
            }, {
                "id": 27,
                "name": "device 27",
                "active": 1
            }]
        
            }, {
            "id": "3",
            "name": "group 3",
            "devices": [{
                "id": 31,
                "name": "device 31",
                "active": 1
            }, {
                "id": 32,
                "name": "device 32",
                "active": 0
            }, {
                "id": 33,
                "name": "device 33",
                "active": 1
            }, {
                "id": 34,
                "name": "device 34",
                "active": 0
            }, {
                "id": 35,
                "name": "device 35",
                "active": 0
            }, {
                "id": 36,
                "name": "device 36",
                "active": 1
            }, {
                "id": 37,
                "name": "device 37",
                "active": 1
            }]
        
            }],
            
            "protocols": [ {
                "id": 1,
                "name": "Modbus"
            },{
                "id": 2,
                "name": "DNP 3"
            },{
                "id": 3,
                "name": "IEC104"
            },{
                "id": 4,
                "name": "MMS"
            }],
            
            "times": [ {
                "id": 1,
                "name": "Last 30 minutes"
            },{
                "id": 2,
                "name": "Last Hour"
            },{
                "id": 3,
                "name": "Last 8 hours"
            },{
                "id": 4,
                "name": "Last 24 Hours"
            }]
        }
    }
  },
  methods:{
      async sendForm(){
          let sendprotocols = [];
          let sendevices = [];
           this.cart.selectedProtocols.forEach(protocol => {
                sendprotocols.push(protocol.id);
           });
            this.cart.selectedDevices.forEach(device => {
                    sendevices.push(device.id);
            });
        let ret = await axios.get('/', {  params: {  devices:sendevices , protocols:sendprotocols, time:this.cart.selectedTime.id } })
        
         return false;
      },
      clearAll(){
            this.cart.selectedDevices = [];
            this.cart.selectedProtocols = [];
            this.cart.selectedTime = [];
            this.data.device_groups.forEach(group => {
                group.devices.forEach(element => {
                        if(element.active === 1){
                            element.active = 0
                        }
                });
            });
      },
    pushDeviceToArray(device){
             this.cart.selectedDevices.push(device);
      },
    removeDeviceFromArray(device){
             var el_index = _.findIndex( this.cart.selectedDevices , function(o)  { return o.id == device.id });
             this.cart.selectedDevices.splice(el_index , 1);
      },
    }

};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" >
body{
    font-size: 16px;
}
.label-style{
    margin: 0;
    display: block;
}
a ,a:hover{
text-decoration: none;
}
.btn{
    border-radius: 3px;
    border:1px solid #6d5cfb;
    width: auto;
    max-width: 250px;
      padding: 0.5rem;
      transition: all 0.25s ease;
      display: inline-block;
    &:hover{
        background: #6d5cfb;
        color: #fff;
      
    }
}
ul, li{
    margin: 0;
    padding: 0;
    list-style: none;
}
.index{
    text-align: left;
    .all-box{
        display: flex;
        flex-wrap: wrap;
        
        .box-wrap{
            flex:  0 0 25%;
            &.cart{
                .btns{
                    padding:  15px 0.5rem;
                }
                .cart-title{
                    color: #6d5cfb;
                    text-transform: capitalize;
                    margin: 15px 0;
                }
                .section{
                    border-bottom: 1px solid rgba(109, 92, 251, 0.5);
                    padding-bottom: 15px;
                    &:last-child{
                        border-bottom: none;
                    }
                }
            }
            .box-title{
                color: #fff;
                margin: 0;
                padding: 0.5rem;
                background: #6d5cfb;
            }
            .inner-box-wrap{
            border: 1px solid #6d5cfb;
            border-radius: 3px;
            margin: 0  0.5rem;
            }
            .content-box{
                padding: 1rem;
            }
           
        }

    }
}
@media only screen and (max-width:1000px) {
 .index{ 
     .all-box {
          .box-wrap{
              flex: 0 0 50%;
              margin-bottom: 25px;
          }
        }
    }
}
@media only screen and (max-width:640px) {
 .index{ 
     .all-box {
          .box-wrap{
              flex: 0 0 100%;
            
          }
        }
    }
}
</style>
