<template>
 <div>
   <!-- https://vuetifyjs.com/en/components/app-bars/#fade-image-on-scroll -->
  <v-head>
  <v-card class="overflow-hidden">
    <v-app-bar
      absolute
      color="primary"
      dark
      inverted-scroll
      scroll-target="#scrolling-techniques-8"
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Title</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-app-bar>
    <v-sheet
      id="scrolling-techniques-8"
      class="overflow-y-auto"
      max-height="600"
    >
      <v-container style="height: 1500px;">
      </v-container>
    </v-sheet>
  </v-card>
  </v-head>

   <v-main>
    <!-- https://medium.com/horadecodar/como-fazer-um-tri%C3%A2ngulo-com-css-8621d57f4d35-->

  <div id="triangulo-para-baixo"></div>

  </v-main>

  <v-footer>
    <!-- https://vuetifyjs.com/en/components/data-iterators/#filter -->

<template v-slot:footer>
        <v-toolbar
          class="mt-2"
          color="indigo"
          dark
          flat>
          <v-toolbar-title class="subheading">
            This is a footer
          </v-toolbar-title>
        </v-toolbar>
  </v-footer>
 </div>
</template>

<script>

</script>

<style>
/* css triangulo*/
div {
    display: inline-block;
    margin-right: 50px;
}

#triangulo-para-baixo {
  width: 0; 
  height: 0; 
  border-left: 25px solid transparent;
  border-right: 25px solid transparent;
  border-top: 25px solid #949396;
}
</style>
