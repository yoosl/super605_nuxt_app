<template>
  <div class="container">
    <CBox
      v-bind="mainStyles[colorMode]"
      d="flex"
      w="100vw"
      h="100vh"
      flex-dir="column"
      justify-content="center"
    >
      <CHeading text-align="center" mb="4"> ⚡️ 你好，605 </CHeading>
      <CFlex justify="center" direction="column" align="center">
        <CBox mb="3">
          <CIconButton
            mr="3"
            :icon="colorMode === 'light' ? 'moon' : 'sun'"
            :aria-label="`Switch to ${
              colorMode === 'light' ? 'dark' : 'light'
            } mode`"
            @click="toggleColorMode"
          />
          <CButton left-icon="info" variant-color="blue" @click="showToast">
            创建用户
          </CButton>
        </CBox>
        <CAvatarGroup>
          <CAvatar
            name="Evan You"
            alt="Evan You"
            src="https://pbs.twimg.com/profile_images/1206997998900850688/cTXTQiHm_400x400.jpg"
          >
            <CAvatarBadge size="1.0em" bg="green.500" />
          </CAvatar>
          <CAvatar
            name="Jonathan Bakebwa"
            alt="Jonathan Bakebwa"
            src="https://res.cloudinary.com/xtellar/image/upload/v1572857445/me_zqos4e.jpg"
          >
            <CAvatarBadge size="1.0em" bg="green.500" />
          </CAvatar>
          <CAvatar
            name="Segun Adebayo"
            alt="Segun Adebayo"
            src="https://pbs.twimg.com/profile_images/1169353373012897802/skPUWd6e_400x400.jpg"
          >
            <CAvatarBadge size="1.0em" bg="green.500" />
          </CAvatar>
          <CAvatar src="pop">
            <CAvatarBadge size="1.0em" border-color="papayawhip" bg="tomato" />
          </CAvatar>
        </CAvatarGroup>
        <CButton
          left-icon="close"
          variant-color="red"
          mt="3"
          @click="showModal = true"
        >
          删除账户
        </CButton>
        <CButton as="nuxt-link" to="/users">
          个人
        </CButton>
        <CModal :is-open="showModal">
          <CModalOverlay />
          <CModalContent>
            <CModalHeader>你确定这么做吗?</CModalHeader>
            <CModalBody>删除账户无法撤销</CModalBody>
            <CModalFooter>
              <CButton @click="showModal = false"> 取消 </CButton>
              <CButton
                margin-left="3"
                variant-color="red"
                @click="showModal = false"
              >
                删除用户
              </CButton>
            </CModalFooter>
            <CModalCloseButton @click="showModal = false" />
          </CModalContent>
        </CModal>
      </CFlex>
    </CBox>
  </div>
</template>

<script lang="js">
import {
  CBox,
  CButton,
  CAvatarGroup,
  CAvatar,
  CAvatarBadge,
  CModal,
  CModalContent,
  CModalOverlay,
  CModalHeader,
  CModalFooter,
  CModalBody,
  CModalCloseButton,
  CIconButton,
  CFlex,
  CHeading
} from '@chakra-ui/vue'

export default {
  name: 'IndexPage',
  components: {
    CBox,
    CButton,
    CAvatarGroup,
    CAvatar,
    CAvatarBadge,
    CModal,
    CModalContent,
    CModalOverlay,
    CModalHeader,
    CModalFooter,
    CModalBody,
    CModalCloseButton,
    CIconButton,
    CFlex,
    CHeading
  },
  inject: ['$chakraColorMode', '$toggleColorMode'],
  data () {
    return {
      showModal: false,
      mainStyles: {
        dark: {
          bg: 'gray.700',
          color: 'whiteAlpha.900'
        },
        light: {
          bg: 'white',
          color: 'gray.900'
        }
      }
    }
  },
  computed: {
    colorMode () {
      return this.$chakraColorMode()
    },
    theme () {
      return this.$chakraTheme()
    },
    toggleColorMode () {
      return this.$toggleColorMode
    }
  },
  methods: {
    showToast () {
      this.$toast({
        title: '账户创建了！',
        description: "我们有一个惊喜给你！",
        status: 'success',
        duration: 3000,
        isClosable: true
      })
    }
  }
}
</script>
