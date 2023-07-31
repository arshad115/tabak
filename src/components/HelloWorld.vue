<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>Caculate percentages for the Shisha Tabak</p>
    <h3>
      Tabak - <span style="color: red">{{ tabakPercentage }}%</span>
    </h3>
    <ul>
      <li>
        <label for="tabak">Tabak:</label>
        <input
          type="number"
          id="tabak"
          name="tabak"
          v-model.number="tabakWeight"
        />
      </li>
      <li>
        <label for="molasse">Molasse:</label>
        <input
          type="number"
          id="molasse"
          name="molasse"
          v-model.number="molasseWeight"
        />
      </li>
    </ul>
    <h3>
      Molasse - <span style="color: red">{{ molassePercentage }}%</span>
    </h3>
    <ul>
      <li>
        <label for="glycerin">Glycerin:</label>
        <input
          type="number"
          id="glycerin"
          name="glycerin"
          v-model.number="glycerinWeight"
        />
      </li>
      <li>
        <label for="aroma">Aroma:</label>
        <input
          type="number"
          id="aroma"
          name="aroma"
          v-model.number="aromaWeight"
        />
      </li>
      <li>
        <label for="sugar">Süßungsmittel:</label>
        <input
          type="number"
          id="sugar"
          name="sugar"
          v-model.number="sugarWeight"
        />
      </li>
    </ul>
    <h3>Values in Percentages</h3>
    <h3>Tabak</h3>
    <ul>
      <li>
        <label for="tabakpercentage">Tabak:</label>
        <input
          type="number"
          id="tabakpercentage"
          name="tabakpercentage"
          v-model.number="tabakPercentage"
        />
      </li>
      <li>
        <label for="molassepercentage">Molasse:</label>
        <input
          type="number"
          id="molassepercentage"
          name="molassepercentage"
          v-model.number="molassePercentage"
        />
      </li>
    </ul>
    <h3>Molasse</h3>
    <ul>
      <li>
        <label for="glycerinpercentage">Glycerin:</label>
        <input
          type="number"
          id="glycerinpercentage"
          name="glycerinpercentage"
          v-model.number="glycerinPercentage"
        />
      </li>
      <li>
        <label for="aromapercentage">Aroma:</label>
        <input
          type="number"
          id="aromapercentage"
          name="aromapercentage"
          v-model.number="aromaPercentage"
        />
      </li>
      <li>
        <label for="sugarpercentage">Süßungsmittel:</label>
        <input
          type="number"
          id="sugarpercentage"
          name="sugarpercentage"
          v-model.number="sugarPercentage"
        />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  computed: {
    molasseWeight: {
      get: function () {
        return (
          (this.tabakWeight / this.tabakPercentage) *
          this.molassePercentage
        ).toFixed(2);
      },
      set: function (newValue) {
        this.molasseWeight = newValue;
      },
    },
    glycerinWeight: {
      get: function () {
        return ((this.molasseWeight / 100) * this.glycerinPercentage).toFixed(
          2
        );
      },
      set: function (newValue) {
        this.glycerinWeight = newValue;
      },
    },
    aromaWeight: {
      get: function () {
        return ((this.molasseWeight / 100) * this.aromaPercentage).toFixed(2);
      },
      set: function (newValue) {
        this.aromaWeight = newValue;
      },
    },
    sugarWeight: {
      get: function () {
        return ((this.molasseWeight / 100) * this.sugarPercentage).toFixed(2);
      },
      set: function (newValue) {
        this.aromaWeight = newValue;
      },
    },
  },
  data() {
    return {
      tabakWeight: 100,
      tabakPercentage: 17,
      molassePercentage: 83,
      glycerinPercentage: 85,
      aromaPercentage: 10,
      sugarPercentage: 5,
    };
  },
  watch: {
    // molasseWeight() {
    //   this.calculate();
    // },
    // tabakWeight() {
    //   this.calculate();
    // },
  },
  methods: {
    calculate: function () {
      this.tabakWeight =
        (this.molasseWeight / this.molassePercentage) * this.tabakPercentage;
      this.molasseWeight =
        (this.tabakWeight / this.tabakPercentage) * this.molassePercentage;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
