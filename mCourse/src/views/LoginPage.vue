<script>
import { mapActions } from "pinia";
import { useCounterStore } from "../stores/counter";
import { GoogleLogin } from "vue3-google-login";

export default {
  data() {
    return {
      dataInput: {
        email: "",
        password: "",
      },
    };
  },
  methods: {
    ...mapActions(useCounterStore, ["forLogin", "handleGoogleLogin"]),
    formLogin() {
      this.forLogin(this.dataInput);
    },
    callback(response) {
      console.log(response);
      this.handleGoogleLogin(response);
    },
  },
};
</script>
<template>
  <!-- <GoogleLogin :callback="callback" prompt /> -->
  <div class="container mx-auto">
    <div class="mx-auto">
      <h1 class="text-center font-bold text-xl mt-16">
        Login To Account mCourse
      </h1>
    </div>
    <div
      class="p-5 border border-black bg-white w-2/5 mx-auto mt-2 shadow pt-10"
    >
      <div class="mx-auto text-center">
        <button
          class="bg-white p-2 m-1 border border-black text-black font-bold w-3/4 hover:bg-slate-50 hover:border hover:border-black hover:text-black text-center"
        >
          <p class="text-center">
            <img
              src="../assets/github.png"
              alt=""
              class="object-fill h-7 mx-auto"
            />
            <a
              href="https://github.com/login/oauth/authorize?client_id=820861e553b218e64fcd"
              class="px-2"
            >
              Login With Github</a
            >
          </p>
        </button>
        <button
          class="bg-white p-2 border border-black text-black font-bold w-3/4 hover:bg-slate-50 hover:border hover:border-black hover:text-black text-center"
        >
          <p class="text-center">
            <img
              src="../assets/GOOGLE.png"
              alt=""
              class="object-fill h-4 mx-auto"
            />
            <GoogleLogin :callback="callback" prompt>
              <span class="px-2"> Login With Google</span>
            </GoogleLogin>
          </p>
        </button>
        <input
          v-model="dataInput.email"
          type="text"
          class="bg-white border border-black w-3/4 p-2 px-2 m-1 placeholder:text-black placeholder:font-semibold"
          placeholder="Email"
        />
        <input
          v-model="dataInput.password"
          type="Password"
          class="bg-white border border-black w-3/4 p-2 px-2 m-1 placeholder:text-black placeholder:font-semibold focus:border"
          placeholder="Password"
        />
        <br />
        <button
          @click.prevent="formLogin"
          class="bg-black p-2 border border-black text-white font-bold w-3/4 hover:bg-slate-50 hover:border hover:border-black hover:text-black"
        >
          LOGIN
        </button>
        <div class="m-2 p-2">
          <label for=""
            >If You Forgot Password
            <RouterLink to="/forgot" class="font-bold hover:text-gray-600"
              >Click Here</RouterLink
            ></label
          >
          <hr class="w-3/4 mx-auto" />
        </div>
        <div>
          <label for=""
            >Don't have Account
            <RouterLink
              to="/register"
              href=""
              class="font-bold hover:text-gray-600"
              >Register Here</RouterLink
            ></label
          >
        </div>
      </div>
    </div>
  </div>
</template>
