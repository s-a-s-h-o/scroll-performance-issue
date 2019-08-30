<template>
    <div slot="content" class="demoContainer" style="height:100%">
      <v-app style="height:100%">
        <v-content>
          <DynamicScroller
            ref="dynamicScroller"
            :items="jobs"
            :min-item-size="100"
            :buffer="500"
            key-field="ID"
            class="scroller custom-scrollable-area"
            style="height:100%"
          >

            <template v-slot="{ item, index, active }">
              <DynamicScrollerItem
                :item="item"
                :active="active"
                :data-index="index"
                style="padding-bottom: 1rem;"
              >
                <div class="cardWrap">
                  <v-card class="my-padding">
                    <v-row>
                      <v-col cols="2" class="d-none d-md-block pa-0">
                        <div class="my-avatar">
                          <MyAvatar :imageSrc="item.logo" />
                        </div>
                      </v-col>
                      <v-col class="col-sm-12 col-md-10 pa-0">
                         <v-row class="d-none d-md-flex pb-3">
                          <v-col cols="8" class="title-and-address p-0">
                            <CardAddress  class="address-desktop" />
                          </v-col>
                          <v-col cols="4" class="chips-and-buttons p-0">
                            <v-row align="center">
                              <v-col cols="2" class="p-0">
                                <v-chip
                                  color="#f2f2f2"
                                  class="ma-0 count-chip"
                                >2</v-chip>
                              </v-col>
                              <v-col cols="8" class="p-0 d-flex rm-justify-center">
                                <v-chip
                                  class="font-size rm-text-color font-weight custom-gradient-light-blue p-0"
                                  text-color="white"
                                >demo btn</v-chip>

                              </v-col>
                              <v-col cols="2" class="p-0">
                                <div class="more-button-holder">
                                  <img src="" alt class="more-button" />
                                </div>
                              </v-col>
                            </v-row>
                          </v-col>
                        </v-row>

                        <v-divider class="my-4 d-flex d-md-none justify-center"></v-divider>

                        <CardAddress
                          class="my-4 d-flex d-md-none justify-center"
                        />

                        <!-- mobile version -->

                        <v-row>
                          <v-col class="pa-0">
                            <v-card class="d-flex flex-wrap fullWidth" flat flex>
                              <CardContent :cardData="item" />
                            </v-card>
                          </v-col>
                        </v-row>
                      </v-col>
                    </v-row>
                  </v-card>

                  <div class="shadow-wrapper" v-if="item.SurveysCount != null ">
                    <div class="shadow-color shadow-1 border-bottom-radius"></div>
                    <div class="shadow-color shadow-2 border-bottom-radius"></div>
                  </div>
                </div>
              </DynamicScrollerItem>
            </template>
          </DynamicScroller>
        </v-content>
      </v-app>
    </div>

</template>

<script>
import CardAddress from '@/components/CardAddress'
import CardContent from '@/components/CardContent'
import MyAvatar from '@/components/my-avatar'

// import layouts


export default {
  components: {
    CardAddress,
    CardContent,
    MyAvatar,
  },
  methods: {
    setBadgeCallback() {}
  },
  computed: {

    jobs() {
      var jobs = []
      for (var k = 0; k < 300; k++) {
       jobs.push({
            ID: k,
            logo: ''
        })}
        return jobs
    },

  }
}
</script>
<style>
html, body{
  overflow: hidden;
  height: 100%;
}
#__nuxt, #__layout, .v-content__wrap{
  height: 100%;
}
.my-padding {
  padding: 1.43rem;
}
/* shadows styles*/
.shadow-color {
  background-color: rgba(128, 128, 128, 0.171);
}
.shadow-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
  padding-bottom: 1rem;
  margin: 0 auto;
}
.shadow-1 {
  width: 98%;
  height: 0.72rem;
}
.shadow-2 {
  width: 95%;
  height: 1.44rem;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  margin: 0 auto;
}


.fullWidth {
  width: 100%;
}


</style>
<style>
/* IE11 flex overflow bug workaround */
#card-slider .v-content__wrap {
  flex: 1 1 0rem !important;
}
/* horizontal slider job cards */
.owl-dot.active > span {
  background: #989898 !important;
}
.row {
  margin-right: 0px;
  margin-left: 0px;
}

.demoContainer {
  height: 100%;
  position: relative;
  overflow-x: hidden;
}
.boxShadowMainContainer {
  box-shadow: 1px 2px 5px 0px rgba(29, 29, 29, 0.07059);
}
.theme--dark{
  background-color: gray!important;
}
</style>
<style scoped>
/* overrides vuetify */
>>> .v-application {
  height: 100%;
  background: transparent !important;
}
>>> .v-application--wrap {
  height: 100%;
  min-height: initial !important;
}
>>> .v-content {
  height: 100%;
}
</style>
