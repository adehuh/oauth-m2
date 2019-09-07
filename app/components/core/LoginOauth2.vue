<template>
     <StackLayout height="100%" width="100%">
   
<Button text="Login" class="btn btn-primary "  @tap="openLogin" />

  </StackLayout>
</template>

<script>
import { configureTnsOAuth } from "nativescript-oauth2";

import {
  TnsOaProvider,
  TnsOaProviderOptionsFacebook,
  TnsOaProviderFacebook,
  TnsOaProviderOptionsGoogle,
  TnsOaProviderGoogle,
  TnsOaProviderOptionsMicrosoft,
  TnsOaProviderMicrosoft
} from "nativescript-oauth2/providers";

import { TnsOAuthClient, ITnsOAuthTokenResult } from "nativescript-oauth2";

export default {
  components: {},
  mounted() {
    console.log(111111111111111111111111111);
    configureTnsOAuth([this.configureOAuthProviderGoogle()]);
    console.log(222222);
  },
  data() {
    return {};
  },
  methods: {
    openLogin() {
      console.log(">>>>>>>>");
      var providerType = "google"; //'google', 'facebook', 'microsoft',
      this.tnsOauthLogin(providerType);
    },
    tnsOauthLogin(providerType) {
     const client = new TnsOAuthClient(providerType);
      client.loginWithCompletion(function(tokenResult, error) {
        if (error) {
          console.error("back to main page with error: ");
          console.error(error);
        } else {
          console.log("back to main page with access token: ");
          console.log(tokenResult);
        }
      });
    },
    configureOAuthProviderGoogle() {
      const googleProviderOptions = {
        openIdSupport: "oid-full",
        clientId:
          "411282977902-35eeg8vsgorkgcq81v518b7u88quchbg.apps.googleusercontent.com",
        redirectUri: "com.googleusercontent.apps.411282977902-35eeg8vsgorkgcq81v518b7u88quchbg:/auth",// kay berhasil;
        //redirectUri: "http://localhost:9000/oauth2/authorization/oidc",
        urlScheme:
          "com.googleusercontent.apps.411282977902-35eeg8vsgorkgcq81v518b7u88quchbg",
        scopes: ["email"]
      };
      const googleProvider = new TnsOaProviderGoogle(googleProviderOptions);
      return googleProvider;
    }
  }
};
</script>

<style>

</style>
