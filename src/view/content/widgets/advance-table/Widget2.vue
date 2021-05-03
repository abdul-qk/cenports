<template>
  <!--begin::Advance Table Widget 2-->
  <div class="card card-custom card-stretch gutter-b">
    <!--begin::Header-->
    <div class="row">
      <div class="col-8 vert-line">
        <div class="card-header d-flex justify-content-between border-0 pt-8">
          <h3 class="card-title align-items-start flex-column my-auto">
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
                  <g
                    stroke="none"
                    stroke-width="1"
                    fill="none"
                    fill-rule="evenodd"
                  >
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
                  <g
                    stroke="none"
                    stroke-width="1"
                    fill="none"
                    fill-rule="evenodd"
                  >
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
      </div>
      <div
        class="col-12 col-lg-4  d-flex justify-content-center flex-column text-center align-items-center"
      >
        <div class="mt-5 mt-lg-0">
          <div
            class="col-12 col-lg-12 d-flex justify-content-center flex-column text-center align-items-center"
          >
            <div class="row">
              <div class="col-12 d-flex my-auto flex-column">
                <h2 class="my-auto">$25,200</h2>
                <p class="my-auto"><strong>Budget:</strong> 56,800</p>
              </div>
            </div>
            <div class="row">
              <div class="col-12 d-flex my-auto flex-column">
                <apexchart
                  class="card-rounded-bottom"
                  :options="chartOptions2"
                  :series="series2"
                  type="area"
                ></apexchart>
              </div>
            </div>
            <div class="row">
              <div
                class="col-12 d-flex my-auto flex-column"
                style="margin-left: 5%;"
              >
                <button class="btn btn-info mt-lg-5">Increase Budget</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!--end::Advance Table Widget 2-->
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "widget-2",
  data() {
    return {
      strokeColor: "#8950FC",
      chartOptions: {},
      chartOptions2: {},
      series: [
        {
          name: "Earning",
          data: [-40, -40, -30, -30, -35, -35],
        },
        {
          name: "Expense",
          data: [13, 23, 20, 8, 13, 27],
        },
      ],
      series2: [
        {
          name: "Earning",
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
        height: 350,
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
          color: "#78909C",
          height: 1,
          width: "100%",
          offsetX: 0,
          offsetY: 0,
        },
        axisTicks: {
          show: true,
          borderType: "solid",
          color: "#78909C",
          height: 6,
          offsetX: 0,
          offsetY: 0,
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
        min: -70,
        max: 70,
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
    this.chartOptions2 = {
      chart: {
        type: "area",
        height: 100,
        toolbar: {
          show: false
        },
        zoom: {
          enabled: false
        },
        sparkline: {
          enabled: true
        }
      },
      plotOptions: {},
      legend: {
        show: false
      },
      dataLabels: {
        enabled: false
      },
      fill: {
        type: "gradient",
        opacity: 1,
        gradient: {
          type: "vertical",
          shadeIntensity: 0.55,
          gradientToColors: ['#fff'],
          inverseColors: true,
          opacityFrom: 1,
          opacityTo: 0.2,
          stops: [25, 50, 100],
          colorStops: []
        }
      },
      stroke: {
        curve: "smooth",
        show: true,
        width: 3,
        colors: [this.strokeColor]
      },
      xaxis: {
        categories: ["Feb", "Mar", "Apr", "May", "Jun", "Jul"],
        axisBorder: {
          show: false
        },
        axisTicks: {
          show: false
        },
        labels: {
          show: false,
          style: {
            colors: this.layoutConfig("colors.gray.gray-500"),
            fontSize: "12px",
            fontFamily: this.layoutConfig("font-family")
          }
        },
        crosshairs: {
          show: false,
          position: "front",
          stroke: {
            color: this.layoutConfig("colors.gray.gray-300"),
            width: 1,
            dashArray: 3
          }
        },
        tooltip: {
          enabled: true,
          formatter: undefined,
          offsetY: 0,
          style: {
            fontSize: "12px",
            fontFamily: this.layoutConfig("font-family")
          }
        }
      },
      yaxis: {
        show: false,
        min: 0,
        max: 37,
        labels: {
          show: false,
          style: {
            colors: this.layoutConfig("colors.gray.gray-500"),
            fontSize: "12px",
            fontFamily: this.layoutConfig("font-family")
          }
        }
      },
      states: {
        normal: {
          filter: {
            type: "none",
            value: 0
          }
        },
        hover: {
          filter: {
            type: "none",
            value: 0
          }
        },
        active: {
          allowMultipleDataPointsSelection: false,
          filter: {
            type: "none",
            value: 0
          }
        }
      },
      tooltip: {
        style: {
          fontSize: "12px",
          fontFamily: this.layoutConfig("font-family")
        },
        y: {
          formatter: function(val) {
            return "$" + val + " thousands";
          }
        },
        marker: {
          show: false
        }
      },
      colors: ['#e9deff'],
      markers: {
        colors: ['#e9deff'],
        strokeColor: [this.strokeColor],
        strokeWidth: 3
      },
      grid: {
        show: false,
        padding: {
          left: 0,
          right: 0
        }
      }
    };
  },
};
</script>
