<script setup>
import { ref ,reactive} from 'vue'

const text=ref(' ')
const author=ref(' ')
const a =ref('')
const address=reactive({"ip":'',
"country":'',
"city":'',
"operator":''
})
function cite(){
fetch('https://v1.hitokoto.cn')
.then(response => response.json())
  .then(data => {
      author.value=data.from_who;
      text.value=data.hitokoto;
    })
    .catch(console.error)

}
function Ipaddress() {
fetch('https://api.vore.top/api/IPdata')
.then(response => response.json())
  .then(data => {
  address.city=data.ipdata.info1+' '+data.ipdata.info2+' '+data.ipdata.info3;
  address.country=data.country;
  address.ip=data.ipinfo.text;
  address.operator=data.ipdata.isp;
  a.value=data;
  })

}

function otherIpaddress() {
fetch('https://api.vore.top/api/IPdata')
.then(response => response.json())
  .then(data => {
  address.city=data.ipdata.info1+' '+data.ipdata.info2+' '+data.ipdata.info3;
  address.country=data.country;
  address.ip=data.ipinfo.text;
  address.operator=data.ipdata.isp;
  a.value=data;
  })

}


</script>



<template>

<div id="quto">
<button @click="cite">Citting</button>
<p>{{text}}</p>
<p id="author">{{author}}</p>
</div>

<div id="ip_address">
<p id="warning">Warning:This function can only be used in China (mainland), couldn't work when inputting foreign Ip address </p>
<button @click="Ipaddress">Get your Ip address</button>
<p>your IP is : {{address.ip}}</p>
<p>your city is : {{address.city}}</p>
<p>your operator is : {{address.operator}}</p>
</div>

</template>

<style>
#quto {
border-color: aquamarine;
border-style: groove;
}

#author{
text-align: right;
font-family: 'songti';
color: brown;
}

#warning {
font-size: 20px;
color:red;
background-color: black;
font-family: 'Times New Roman';
font-weight: 560;

}
</style>