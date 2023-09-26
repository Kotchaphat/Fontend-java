<template>
  <v-card>
    <v-card-title style="font-size: 20px;">เข้าสู่ระบบ</v-card-title>
    <v-card-text>
    <v-form ref="form" v-model="valid" lazy-validation>
      <v-text-field
        v-model="name"
        :counter="10"
        :rules="nameRules"
        label="ชื่อผู้ใช้งาน"
        placeholder="กรุณากรอกชื่อผู้ใช้"
        required
      ></v-text-field>

      <v-text-field
        v-model="email"
        :rules="emailRules"
        label="รหัสผ่าน"
        required
      ></v-text-field>

     

      <v-checkbox
        v-model="checkbox"
        :rules="[(v) => !!v || 'You must agree to continue!']"
        label="ยอมรับเงื่อนไข"
        required
      ></v-checkbox>

      <v-btn :disabled="!valid" 
      color="success" class="mr-4" 
      @click="Login" 
      block>
        เข้าสู่ระบบ
      </v-btn>

     
    </v-form>
</v-card-text>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    valid: true,
    name: "",
    nameRules: [
      (v) => !!v || "กรุณากรอกชื่อผู้ใช้งาน",
      (v) => (v && v.length <= 10) || "กรุณากรอกชื่อผู้ใช้งานห้ามเกิน 10 อักษร",
    ],
    email: "",
    emailRules: [
      (v) => !!v || "กรุณากรอกรหัสผ่าน",
     
    ],
    
  }),

  methods: {
    Login(){
            if(this.$refs.loginpage.validate(true)){
                localStorage.setItem('username',this.name)
                this.$EventBus.$emit('getUsername')
                this.$router.push('/')
              //  alert('ผ่าน')
                 //       }else{
                  //  this.alert('ไม่ผ่าน')  
                }          
     alert('เข้าสู่ระบบ')   
    },
    
  },
};
</script>

<style>
</style>