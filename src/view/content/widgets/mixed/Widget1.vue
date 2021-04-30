<template>
  <!--begin::Mixed Widget 1-->
  <div class="card card-custom gutter-b">
    <!--begin::Header-->
    <div class="card-header border-0 py-5 d-flex">
      <h3 class="card-title my-auto font-weight-bolder">
        Reports
      </h3>
      <p class="font-weight-light my-auto">Updated 1 month ago</p>
    </div>
    <!--end::Header-->
    <!--begin::Body-->
    <div class="card-body p-0 position-relative mt-15">
      <!--begin::Stats-->
      <div class="card-spacer mt-n25">
        <!--begin::Row-->
        <div class="row mb-2">
          <div
            class="col bg-light-warning my-auto rounded-xl mr-7 mb-7 d-flex py-4"
          >
            <span
              class="svg-icon svg-icon-3x svg-icon-warning d-block my-2 pr-5"
            >
              <inline-svg src="media/svg/icons/Shopping/Chart-line1.svg" />
            </span>
            <div class="d-flex flex-column">
              <a href="#" class="text-warning font-weight-bold font-size-h6">
                Sales
              </a>
              <p class="text-dark font-weight-bold mt-2">230k</p>
            </div>
          </div>
          <div class="col bg-light-primary my-auto rounded-xl mb-7 d-flex py-4">
            <span class="svg-icon svg-icon-3x svg-icon-primary d-block my-2">
              <inline-svg src="media/svg/icons/Communication/Add-user.svg" />
            </span>
            <div class="d-flex flex-column">
              <a
                href="#"
                class="text-primary font-weight-bold font-size-h6 mt-2"
              >
                Customers
              </a>
              <p class="text-dark font-weight-bold mt-2">8.459K</p>
            </div>
          </div>
        </div>
        <!--end::Row-->
        <!--begin::Row-->
        <div class="row mb-2">
          <div class="col bg-light-danger my-auto rounded-xl mr-7 d-flex py-4">
            <span class="svg-icon svg-icon-3x svg-icon-danger d-block my-2">
              <inline-svg src="media/svg/icons/Design/Layers.svg" />
            </span>
            <div class="d-flex flex-column">
              <a
                href="#"
                class="text-danger font-weight-bold font-size-h6 mt-2"
              >
                Products
              </a>
              <p class="text-dark font-weight-bold mt-2">1.423k</p>
            </div>
          </div>
          <div class="col bg-light-success my-auto rounded-xl d-flex py-4">
            <span class="svg-icon svg-icon-3x svg-icon-success d-block my-2">
              <inline-svg src="media/svg/icons/Shopping/Dollar.svg" />
            </span>
            <div class="d-flex flex-column">
              <a
                href="#"
                class="text-success font-weight-bold font-size-h6 mt-2"
              >
                Revenue
              </a>
              <p class="text-dark font-weight-bold mt-2">$9745</p>
            </div>
          </div>
        </div>
        <!--end::Row-->
      </div>
      <!--end::Stats-->
      <!--end::Body-->
    </div>
    <!--end::Mixed Widget 1-->
  </div>
</template>

<script>
// import Dropdown1 from "@/view/content/dropdown/Dropdown1.vue";
import { mapGetters } from "vuex";

export default {
  name: "widget-1",
  components: {
    // Dropdown1
  },
  data() {
    return {
      strokeColor: "#D13647",
      chartOptions: {},
      series: [
        {
          name: "Net Profit",
          data: [30, 45, 32, 70, 40, 40, 40]
        }
      ]
    };
  },
  computed: {
    ...mapGetters(["layoutConfig"])
  },
  mounted() {
    // reference; kt_mixed_widget_1_chart
    this.chartOptions = {
      chart: {
        type: "area",
        height: 150,
        toolbar: {
          show: false
        },
        zoom: {
          enabled: false
        },
        sparkline: {
          enabled: true
        },
        dropShadow: {
          enabled: true,
          enabledOnSeries: undefined,
          top: 5,
          left: 0,
          blur: 3,
          color: this.strokeColor,
          opacity: 0.5
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
        type: "solid",
        opacity: 0
      },
      stroke: {
        curve: "smooth",
        show: true,
        width: 3,
        colors: [this.strokeColor]
      },
      xaxis: {
        categories: ["Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug"],
        axisBorder: {
          show: false
        },
        axisTicks: {
          show: false
        },
        tooltip: {
          enabled: false
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
        }
      },
      yaxis: {
        show: false,
        min: 0,
        max: 80,
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
      colors: ["transparent"],
      markers: {
        colors: [this.layoutConfig("colors.theme.light.danger")],
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
  }
};
</script>
