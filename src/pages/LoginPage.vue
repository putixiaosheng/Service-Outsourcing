<template>
    <div class="home">
      <a-form :model="form"  @submit="handleSubmit" class="login_form" size="large  ">
          <a-icon type="user" />
        <a-form-item field="name"  label="Username" >
          <template #label>
            <div style="color: white;font-size: 12px;float: right;">
              Username
            </div>
          </template>
          <a-input
            v-model="form.name"
            placeholder="please enter your username..."
          />
        </a-form-item>
        <a-form-item field="passowrd" label="Password">
          <template #label>
            <div style="color: white;font-size: 12px;float: right;">
              Password
            </div>
          </template>
          <a-input v-model="form.post" placeholder="please enter your password..." />
        </a-form-item>
        <a-form-item field="confirmPassowrd" label="comfirmPassword" v-if="type==2">
          <template #label>
            <div style="color: white;font-size: 12px;width: 100px;float: right;">
              ConfirmPassword
            </div>
          </template>
          <a-input v-model="form.post" placeholder="please enter your password again..." />
        </a-form-item>
        <a-form-item hide-label>
          <div style="width: 100%;display: flex;justify-content: center;">
            <a-button html-type="submit" style="width: 80%;" type="primary" @click="onSubmit">Login</a-button>
          </div>
        </a-form-item>
        <a-form-item hide-label>
          <div class="tip" @click="goRegister" v-if="type==1">
            Not registered yet, please click here
          </div>
          <div class="tip" @click="goLogin" v-if="type==2">
            Existing account? Click here to log in
          </div>
        </a-form-item>
      </a-form>
    </div>
  </template>
  
  <script setup>
  import { onMounted, onUpdated, reactive,ref } from 'vue'
  import { useRouter } from 'vue-router'
// do not use same name with ref
const type = ref(1)
const router = useRouter()
const form = reactive({
  name: '',
  password: '',
  confirmPassword: ''
})
 
const onSubmit = () => {
    router.push('/main')
}

const goRegister = () => {
  router.replace('/login?type=2')
}
const goLogin = () => {
  router.replace('/login?type=1')
}
onMounted(() => {
  type.value = router.currentRoute.value.query.type

})
onUpdated(() => {
  type.value = router.currentRoute.value.query.type
  console.log(router.currentRoute.value.query.type)
  console.log(type.value)
})
  </script>
  <style>
  body {
    height: 100vh;
    width: 100vw;
    background-image: url('../assets/loginbackgroud.jpg');
    background-repeat: no-repeat; /* 不重复平铺背景图片 */
    background-position: center; /* 居中显示背景图片 */
    background-size: cover;
  }
  .home {
    width: 400px !important;
    height: 300px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: rgba(10,81,192,0.5);
    border-radius: 20px;
    box-shadow: 0 0 20px rgba(0,0,0,0.5);
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .login_form {
    width: 70% !important;
  }
  .tip{
    text-align: center;
    width: 100%;
    color: white;
  }
  body {
    height: 100vh;
    width: 100vw;
    background-image: url('../assets/loginbackgroud.jpg');
    background-repeat: no-repeat; /* 不重复平铺背景图片 */
    background-position: center; /* 居中显示背景图片 */
    background-size: cover;
  }
  .home {
    width: 400px !important;
    height: 300px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: rgba(10,81,192,0.5);
    border-radius: 20px;
    box-shadow: 0 0 20px rgba(0,0,0,0.5);
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .login_form {
    width: 70% !important;
  }
  .tip{
    text-align: center;
    width: 100%;
    color: white;
  }
</style>