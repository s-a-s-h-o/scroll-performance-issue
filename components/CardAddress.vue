<template>
  <div class="address">
    <div class="address-location">
      <div>
        <img src="" />
      </div>
      <div>{{ getLocationAddress}}</div>
    </div>
  </div>
</template>

<script>
export default {

  name: 'CardAddress',
  computed: {
    getLocationAddress() {
      return "Some address"
    },
  },
  methods: {}
}
</script>

<style scoped>
.address {
  text-align: left;
  font-size: 1rem;
  color: #3a3a3a;
  font-weight: normal;
}
.address-location {
  cursor: pointer;
  line-height: 1.4285rem;
  display: flex;
  flex-direction: row;
}
.address-location img {
  margin-top: -3px;
  margin-right: 5px;
}
.missing-location {
  color: #999999;
  display: inline;
}
</style>
