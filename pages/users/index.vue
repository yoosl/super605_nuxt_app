<template>
  <CStack :spacing="5" direaction="column">
    <c-box v-for="(message, index) in messages" :key="index" w="300px" shadow="md" rounded="lg" p="5" >
      <c-image rounded="md" src="https://bit.ly/2k1H1t6"/>
      <c-flex mt="2">
        <c-avatar :src="static_host + '/images/' + message.avatar_img" />
        <c-box ml="3">
          <c-text font-weight="bold">
            {{ message.name }}
            <c-badge ml="1" variant-color="green">
              NEW
            </c-badge>
          </c-text>
          <c-text font-size="sm">{{ message.occupation }}</c-text>
        </c-box>
      </c-flex>
      <c-text mt="2" font-size="xl" font-weight="semibold" line-height="short">
        {{ message.title }}
      </c-text>
      <!-- <c-text mt="2">$119/night</c-text> -->
      <c-flex mt="2" align="center">
        <c-icon name="star" color="orange.400" />
        <c-text ml="1" font-size="sm"><b>4.84</b> (190)</c-text>
      </c-flex>
      <c-flex mt="2">
        <c-button @click="loadData">查看</c-button>
      </c-flex>
    </c-box>
  </CStack>
</template>

<script>
  import {
  CAvatar,
  CStack,
  CBox,
  CButton,
  CBadge,
  CFlex,
  CImage,
  CText,
} from '@chakra-ui/vue'

  import axios from 'axios'
  axios.defaults.baseURL = "http://192.168.3.4:3030"
  export default {
    name: 'UsersPage',
    components:{
      CAvatar,
      CStack,
      CBox,
      CButton,
      CBadge,
      CFlex,
      CImage,
      CText,
    },
    data () {
      axios.get('/usersAndMessages').then((res)=>{
          this.messages = res.data.data
      })
      return {
        messages:[],
        static_host: "http://192.168.3.4:8080",
      }
    },
    methods:{
      loadData(){
        
      }
    },
    
  }
</script>