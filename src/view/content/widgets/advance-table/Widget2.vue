<template>
  <!--begin::Advance Table Widget 2-->
  <div class="card card-custom card-stretch gutter-b">
    <!--begin::Header-->
    <div class="card-header border-0 pt-5">
      <h3 class="card-title align-items-start flex-column">
        <span class="card-label font-weight-bolder text-dark my-auto">
          Revenue Report
        </span>
      </h3>
      <div class="d-flex justify-content-end my-auto">
        <p class="mr-2 my-auto">
          <span class="svg-icon svg-icon-info svg-icon"
            ><svg
              xmlns="http://www.w3.org/2000/svg"
              xmlns:xlink="http://www.w3.org/1999/xlink"
              width="24px"
              height="24px"
              viewBox="0 0 24 24"
              version="1.1"
            >
              <g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                <rect x="0" y="0" width="24" height="24" />
                <circle fill="#000000" cx="12" cy="12" r="8" />
              </g></svg></span
          >Earning
        </p>
        <p class="mr-2 my-auto">
          <span class="svg-icon svg-icon-primary svg-icon"
            ><svg
              xmlns="http://www.w3.org/2000/svg"
              xmlns:xlink="http://www.w3.org/1999/xlink"
              width="24px"
              height="24px"
              viewBox="0 0 24 24"
              version="1.1"
            >
              <g stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
                <rect x="0" y="0" width="24" height="24" />
                <circle fill="#000000" cx="12" cy="12" r="8" />
              </g></svg></span
          >Expense
        </p>
      </div>
    </div>
    <!--end::Header-->
    <!--begin::Body-->
    <div class="card-body">
      <!--begin::Table-->
      <apexchart
        class="card-rounded-bottom"
        :options="chartOptions"
        :series="series"
        type="bar"
      ></apexchart>
      <!--end::Table-->
    </div>
    <!--end::Body-->
    <!--end::Advance Table Widget 2-->
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "widget-2",
  data() {
    return {
      chartOptions: {},
      series: [
        {
          name: "Earning",
          data: [40, 40, 30, 30, 35, 35],
        },
        {
          name: "Expense",
          data: [13, 23, 20, 8, 13, 27],
        },
      ],
    };
  },
  computed: {
    ...mapGetters(["layoutConfig"]),
  },
  mounted() {
    // reference; kt_stats_widget_7_chart
    this.chartOptions = {
      chart: {
        type: "bar",
        height: 250,
        stacked: true,
        toolbar: {
          show: false,
        },
        sparkline: {
          enabled: true,
        },
      },
      plotOptions: {
        bar: {
          horizontal: false,
          columnWidth: ["10%"],
          endingShape: "rounded",
        },
      },
      legend: {
        show: false,
      },
      dataLabels: {
        enabled: false,
      },
      stroke: {
        show: true,
        width: 2,
        borderRadius: 16,
        colors: ["transparent"],
      },
      xaxis: {
        categories: ["Feb", "Mar", "Apr", "May", "Jun", "Jul"],
        axisBorder: {
          show: true,
          color: '#78909C',
          height: 1,
          width: '100%',
          offsetX: 0,
          offsetY: 0
        },
        axisTicks: {
          show: true,
          borderType: 'solid',
          color: '#78909C',
          height: 6,
          offsetX: 0,
          offsetY: 0
        },
        labels: {
          show: true,
          style: {
            colors: this.layoutConfig("colors.gray.gray-500"),
            fontSize: "12px",
            fontFamily: this.layoutConfig("font-family"),
          },
          offsetX: 0,
          offsetY: -20,
        },
      },
      yaxis: {
        min: 0,
        max: 100,
        axisBorder: {
          show: false,
        },
        axisTicks: {
          show: false,
        },
        labels: {
          show: true,
          style: {
            colors: this.layoutConfig("colors.gray.gray-500"),
            fontSize: "12px",
            fontFamily: this.layoutConfig("font-family"),
          },
          offsetX: 20,
          offsetY: 0,
        },
      },
      fill: {
        opacity: 1,
      },
      states: {
        normal: {
          filter: {
            type: "none",
            value: 0,
          },
        },
        hover: {
          filter: {
            type: "none",
            value: 0,
          },
        },
        active: {
          allowMultipleDataPointsSelection: false,
          filter: {
            type: "none",
            value: 0,
          },
        },
      },
      tooltip: {
        style: {
          fontSize: "12px",
          fontFamily: this.layoutConfig("font-family"),
        },
        y: {
          formatter: function(val) {
            return "$" + val + " thousands";
          },
        },
      },
      colors: ["#8950FC", "#3699FF"],
      grid: {
        borderColor: this.layoutConfig("colors.gray.gray-200"),
        strokeDashArray: 4,
        yaxis: {
          lines: {
            show: false,
          },
        },
      },
    };
  },
};
</script>
