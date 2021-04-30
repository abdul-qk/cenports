<template>
  <!--begin::Mixed Widget 14-->
  <div class="card card-custom card-stretch gutter-b">
    <!--begin::Header-->
    <div class="card-header border-0 pt-5">
      <h3 class="card-title font-weight-bolder">Invoice Overview</h3>
    </div>
    <!--end::Header-->
    <!--begin::Body-->
    <div class="card-body d-flex flex-column">
      <div class="flex-grow-1">
        <apexchart
          :options="chartOptions"
          :series="series"
          type="radialBar"
        ></apexchart>
      </div>
      <div>
        <div class="row horz-line pt-3 mb-5">
          <div class="col-6 d-flex flex-column text-center vert-line">
            <p>Completed</p>
            <h3>786,617</h3>
          </div>
          <div class="col-6 d-flex flex-column text-center">
            <p>In Progress</p>
            <h3>13,561</h3>
          </div>
        </div>
        <a
          href="#"
          class="btn btn-success btn-shadow-hover font-weight-bolder w-100 py-3"
          >Generate Report</a
        >
      </div>
    </div>
    <!--end::Body-->
  </div>
  <!--end::Mixed Widget 14-->
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "widget-7",
  data() {
    return {
      chartOptions: {},
      series: [74],
    };
  },
  computed: {
    ...mapGetters(["layoutConfig"]),
  },
  mounted() {
    // reference; kt_stats_widget_7_chart
    this.chartOptions = {
      chart: {
        height: 200,
        type: "radialBar",
      },
      plotOptions: {
        radialBar: {
          hollow: {
            margin: 0,
            size: "65%",
          },
          dataLabels: {
            showOn: "always",
            name: {
              show: false,
              fontWeight: "700",
            },
            value: {
              color: this.layoutConfig("colors.gray.gray-700"),
              fontSize: "30px",
              fontWeight: "700",
              offsetY: 12,
              show: true,
            },
          },
          track: {
            background: this.layoutConfig("colors.theme.light.success"),
            strokeWidth: "100%",
          },
        },
      },
      colors: [this.layoutConfig("colors.theme.base.success")],
      stroke: {
        lineCap: "round",
      },
      labels: ["Progress"],
    };
  },
};
</script>
