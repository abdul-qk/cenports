<template>
  <div
    class="subheader py-2 py-lg-4 subheader-solid"
    v-bind:class="subheaderClasses"
    id="kt_subheader"
  >
    <div
      class="d-flex align-items-center justify-content-between flex-wrap flex-sm-nowrap"
      v-bind:class="{ 'container-fluid': widthFluid, container: !widthFluid }"
    >
      <div class="d-flex align-items-center flex-wrap mr-1">
        <h5 class="text-dark font-weight-bold my-2 mr-5">
          {{ title }}
        </h5>
      </div>
      <div class="d-flex align-items-center">
        <h6 class="mr-5 my-auto">Date</h6>
        <date-picker v-model="value3" range placeholder="Select date range">
          <template v-slot:header="{ emit }">
            <div style="text-align: left">
              <button class="mx-btn mx-btn-text" @click="today(emit)">
                Today</button
              ><button class="mx-btn mx-btn-text" @click="yesterday(emit)">
                Yesterday</button
              ><button class="mx-btn mx-btn-text" @click="lastSevenDays(emit)">
                Last Seven Days</button
              ><button class="mx-btn mx-btn-text" @click="last30Days(emit)">
                Last 30 Days</button
              ><button class="mx-btn mx-btn-text" @click="thisMonth(emit)">
                This Month
              </button>
            </div>
          </template>
        </date-picker>
        <a class="ml-4" href="#">
          <i class="flaticon2-gear"></i>
        </a>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.custom-v-dropdown {
  &.dropdown-toggle {
    padding: 0;
    &:hover {
      text-decoration: none;
    }

    &.dropdown-toggle-no-caret {
      &:after {
        content: none;
      }
    }
  }

  &.dropdown-menu {
    margin: 0;
    padding: 0;
    outline: none;
    .b-dropdown-text {
      padding: 0;
    }
  }
}
</style>

<script>
import { mapGetters } from "vuex";
import DatePicker from "vue2-datepicker";
import "vue2-datepicker/index.css";

export default {
  name: "KTSubheader",
  props: {
    breadcrumbs: Array,
    title: String,
  },
  components: { DatePicker },
  data() {
    return {
      value1: [new Date(), new Date()],
      value2: [],
      value3: [],
      shortcuts: [
        {
          text: "Today",
          onClick() {
            const date = [new Date(), new Date()];
            // return a Date
            return date;
          },
        },
      ],
    };
  },
  methods: {
    today(emit) {
      const start = new Date();
      const end = new Date();
      const date = [start, end];
      emit(date);
    },
    yesterday(emit) {
      const start = new Date();
      const end = new Date();
      start.setTime(end.getTime() - 3600 * 1000 * 24);
      const date = [start, end];
      emit(date);
    },
    lastSevenDays(emit) {
      const start = new Date();
      const end = new Date();
      start.setTime(end.getTime() - 7 * 24 * 3600 * 1000);
      const date = [start, end];
      emit(date);
    },
    last30Days(emit) {
      const start = new Date();
      const end = new Date();
      start.setTime(end.getTime() - 30 * 24 * 3600 * 1000);
      const date = [start, end];
      emit(date);
    },
    thisMonth(emit) {
      const start = new Date(date.getFullYear(), date.getMonth(), 1);
      const end = new Date(date.getFullYear(), date.getMonth() + 1, 0);
      const date = [start, end];
      emit(date);
    },
  },
  computed: {
    ...mapGetters(["layoutConfig"]),

    /**
     * Check if subheader width is fluid
     */
    widthFluid() {
      return this.layoutConfig("subheader.width") === "fluid";
    },

    subheaderClasses() {
      const classes = [];
      const style = this.layoutConfig("subheader.style");
      if (style) {
        classes.push(style);

        if (style === "solid") {
          classes.push("bg-white");
        }

        if (this.layoutConfig("subheader.fixed")) {
          classes.push("border-top");
        }
      }
      return classes.join(" ");
    },
  },
};
</script>
