<template>
  <v-card class="fullWidth" flat>
    <div class="card-content">
      <div
        :class="{
        'first-info-box': isIndexZero(index) && isSingleRow,
        'info-box': !isIndexZero(index) && isSingleRow,
        'first-info-box-quarter':isIndexZero(index) && !isSingleRow,
        'info-box-quarter': !isIndexZero(index) && index < 4 && !isSingleRow,
        'info-box-quarter-second-level first-info-box-quarter':index == 4 && !isSingleRow,
        'info-box-quarter-second-level info-box-quarter': !isIndexZero(index) && index > 4 && !isSingleRow,
        }"
        v-for="(data, index) in cardData"
        :key="index"
      >
        <div class="heading details">{{ data.Name }}</div>
        <div class="details">
          <span class="someNumber">{{ data.Value }}</span>
        </div>

      </div>
    </div>
  </v-card>
</template>

<script>

export default {
  name: 'CardContent',

  computed: {
    cardData(){
      return [
        {
          Name: "Key",
          Value: "Value"
        }, {
            Name: "Key",
            Value: "Value"
        }, {
            Name: "Key",
            Value: "Value"
        }, {
            Name: "Key",
            Value: "Value"
        }, {
            Name: "Key",
            Value: "Value"
        }
    ]

    },
    isSingleRow() {
      return this.cardData.length <= 5 ? true : false
    }
  },
  methods: {
    isIndexZero(index) {
      return index == 0 ? true : false
    },
  }
}
</script>

<style scoped>
.value-prefix {
  display: inline-block;
}
.card-content {
  display: flex;
  flex-direction: row;
  font-family: Roboto;
  flex-wrap: wrap;
}
.first-info-box {
  width: calc(20% - 1rem);
}
.info-box {
  border-left: 1px solid #f2f2f2;
  padding-left: 1rem;
  padding-right: 1rem;
  min-width: 20%;
}

.first-info-box-quarter {
  min-width: 25%;
}
.info-box-quarter {
  border-left: 1px solid #efefef;
  padding-left: 1rem;
  padding-right: 1rem;
  min-width: 25%;
}
.info-box-quarter-second-level {
  margin-top: 1rem;
}

.details {
  text-align: left;
  font-size: 1rem;
}
.heading {
  font-size: 0.78rem;
  text-transform: uppercase;
  color: #bcbcbc;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.someNumber {
  color: #3dd1b1;
  font-weight: bold;
  font-size: 1rem;
}
.overdue-icon,
.today-icon {
  height: 1rem;
}
.overdue {
  color: #fb6042;
  text-transform: uppercase;
}
.today {
  color: #3dd1b1;
  text-transform: uppercase;
}

@media only screen and (max-width: 768px) {
  .info-box {
    border-left: 0px;
    padding: 1rem 0 0;
    width: 50%;
  }
  .first-info-box {
    padding: 1rem 0 0;
    width: 50%;
  }

  .info-box-quarter {
    border-left: 0px;
    padding: 1rem 0 0;
    width: 50%;
  }
  .first-info-box-quarter {
    padding: 1rem 0 0;
    width: 50%;
  }
  .info-box-quarter-second-level {
    margin-top: 0;
  }
}
</style>
