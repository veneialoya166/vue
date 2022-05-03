<template>
  <Suspense>
    <template #default>
      <Home/>
    </template>
     <template #fallback>
       <SplashScreen/>
     </template>
  </Suspense>
</template>

<script>
import SplashScreen from "@/components/SplashScreen.vue"
import { defineAsyncComponent } from "vue";
export default {
  components: {
    SplashScreen,
    Home: defineAsyncComponent(() => 
    new Promise((resolve) => {
      setTimeout(() => {
        resolve(import("./components/Home.vue"))
      }, 2500);

    })
    )
  }
}
</script>

<style>
html,
body,
.app{
  min-height: 100vh;
  margin: 0 auto;
  font-family: Arial, Helvetica, sans-serif;

}
*{
  --brnad-green: #04b500;
  --brnad-blue: #0698b0;
}

</style>
