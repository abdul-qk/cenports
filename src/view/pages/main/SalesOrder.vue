<template>
  <div>
    <div class="card card-custom gutter-b">
      <div class="card-header card-header-tabs-line">
        <ul
          class="nav nav-dark nav-bold nav-tabs nav-tabs-line"
          role="tablist"
          ref="builder-tab"
        >
          <li class="nav-item">
            <a
              class="nav-link active"
              v-on:click="setActiveTab"
              data-tab="0"
              data-toggle="tab"
              href="#"
              role="tab"
            >
              Sales Orders
            </a>
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              v-on:click="setActiveTab"
              data-tab="1"
              data-toggle="tab"
              href="#"
              role="tab"
            >
              Back Orders
            </a>
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              v-on:click="setActiveTab"
              data-tab="2"
              data-toggle="tab"
              href="#"
              role="tab"
            >
              3PL Orders
            </a>
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              v-on:click="setActiveTab"
              data-tab="3"
              data-toggle="tab"
              href="#"
              role="tab"
            >
              Returns
            </a>
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              v-on:click="setActiveTab"
              data-tab="4"
              data-toggle="tab"
              href="#"
              role="tab"
            >
              Deleted Orders
            </a>
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              v-on:click="setActiveTab"
              data-tab="5"
              data-toggle="tab"
              href="#"
              role="tab"
            >
              Cancelled
            </a>
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              v-on:click="setActiveTab"
              data-tab="6"
              data-toggle="tab"
              href="#"
              role="tab"
            >
              Rejected Orders
            </a>
          </li>
        </ul>
      </div>

      <!--begin::Tab Content-->
      <div class="card-body">
        <b-tabs class="hide-tabs" v-model="tabIndex">
          <b-tab active>
            <div class="row">
              <div class="col-lg-4 d-flex flex-column">
                <p>Units Sold During:</p>
                <date-picker
                  v-model="value1"
                  format="YYYY-MM-DD"
                  type="date"
                  placeholder="Select date"
                ></date-picker>
              </div>
              <div class="col-lg-4 d-flex flex-column">
                <p>to:</p>
                <date-picker
                  v-model="value1"
                  format="YYYY-MM-DD"
                  type="date"
                  placeholder="Select date"
                ></date-picker>
              </div>
              <div class="col-lg-4 d-flex align-items-end">
                <button class="btn btn-primary">Search</button>
              </div>
            </div>
            <div class="row mt-5">
              <div class="col-lg-3">
                <div class="card card-body bg-danger text-white">
                  <h4>Unprocessed</h4>
                  <h2>3409</h2>
                </div>
                <apexchart
                  class="card-rounded-bottom"
                  :options="chartOptions"
                  :series="series"
                  type="bar"
                  width="100%"
                ></apexchart>
              </div>
              <div class="col-lg-3">
                <div class="card card-body bg-info text-white">
                  <h4>Shipped</h4>
                  <h2>3409</h2>
                </div>
                <apexchart
                  class="card-rounded-bottom"
                  :options="chartOptions2"
                  :series="series2"
                  type="bar"
                  width="100%"
                ></apexchart>
              </div>
              <div class="col-lg-3">
                <div class="card card-body bg-success text-white">
                  <h4>Cancelled</h4>
                  <h2>3409</h2>
                </div>
                <apexchart
                  class="card-rounded-bottom"
                  :options="chartOptions3"
                  :series="series3"
                  type="bar"
                  width="100%"
                ></apexchart>
              </div>
              <div class="col-lg-3">
                <div class="card card-body bg-warning text-white">
                  <h4>Back Ordered</h4>
                  <h2>3409</h2>
                </div>
                <apexchart
                  class="card-rounded-bottom"
                  :options="chartOptions4"
                  :series="series4"
                  type="bar"
                  width="100%"
                ></apexchart>
              </div>
            </div>

            <!-- Break Content -->
            <hr class="my-20" />
            <!-- End Break Content -->

            <!-- Start: Bottom Content -->
            <div class="row">
              <div class="col-lg-8">
                <div class="row">
                  <div class="col-2">
                    <div style="width: 100%" class="btn-group">
                      <button
                        class="btn btn-secondary font-weight-bold btn-lg dropdown-toggle"
                        type="button"
                        data-toggle="dropdown"
                        aria-haspopup="true"
                        aria-expanded="false"
                      >
                        Filter
                      </button>
                      <div class="dropdown-menu dropdown-menu-lg">
                        <form class="px-8 py-8">
                          <div class="btn-group">
                            <button
                              type="button"
                              class="btn btn-secondary dropdown-toggle"
                              data-toggle="dropdown"
                              aria-haspopup="true"
                              aria-expanded="false"
                            >
                              Action
                            </button>
                            <div class="dropdown-menu">...</div>
                          </div>
                          <button type="submit" class="btn btn-primary">
                            Filter
                          </button>
                        </form>
                      </div>
                    </div>
                  </div>
                  <div class="col-7">
                    <input style="height: 100%" class="form-control" type="text" id="search-keyword" placeholder="Search by Purchase Order No, Customer Order No, Customer Name, Invoice No, Tracking No"/>
                  </div>
                  <div class="col-3 d-flex">
                    <button style="width: 100%" class="btn btn-primary mr-2">Search</button>
                    <button style="width: 100%" class="btn btn-secondary">Clear</button>
                  </div>
                </div>
              </div>
              <div class="col-lg-4 d-flex justify-content-end">
                <button class="btn btn-secondary mr-2">Reset Order(s)</button>
                <button class="btn btn-secondary mr-2">Bulk Print</button>
                <button class="btn btn-secondary">Bulk Update</button>
              </div>
            </div>
            <div class="row mt-8">
              <div class="col-6 d-flex justify-content-start">
                <h4>Showing results for <span class="text-gray results">Unshipped orders</span></h4>
              </div>
              <div class="col-6 d-flex justify-content-end">
                <button class="btn btn-warning">Expand Details</button>
              </div>
            </div>
            <!-- End: Bottom Content -->
          </b-tab>

          <b-tab>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label">
                Desktop Fixed Header:
              </label>
              <div class="col-lg-9 col-xl-4">
                <span class="switch switch-icon">
                  <label>
                    <input
                      type="checkbox"
                      v-model="config.header.self.fixed.desktop"
                      value="true"
                      checked=""
                    />
                    <span></span>
                  </label>
                </span>
                <div class="form-text text-muted">
                  Enable fixed header for desktop mode
                </div>
              </div>
            </div>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label">
                Mobile Fixed Header:
              </label>
              <div class="col-lg-9 col-xl-4">
                <span class="switch switch-icon">
                  <label>
                    <input
                      type="checkbox"
                      v-model="config.header.self.fixed.mobile"
                      value="true"
                      checked=""
                    />
                    <span></span>
                  </label>
                </span>
                <div class="form-text text-muted">
                  Enable fixed header for mobile mode
                </div>
              </div>
            </div>

            <div class="form-group row">
              <label class="col-lg-3 col-form-label">
                Display Header Menu:
              </label>
              <div class="col-lg-9 col-xl-4">
                <span class="switch switch-icon">
                  <label>
                    <input
                      type="checkbox"
                      v-model="config.header.menu.self.display"
                      value="true"
                      checked=""
                    />
                    <span></span>
                  </label>
                </span>
                <div class="form-text text-muted">Display header menu</div>
              </div>
            </div>

            <div class="form-group row">
              <label class="col-lg-3 col-form-label">
                Header Menu Layout:
              </label>
              <div class="col-lg-9 col-xl-4">
                <select
                  class="form-control"
                  v-model="config.header.menu.self.layout"
                >
                  <option value="default" selected="">Default</option>
                  <option value="tab">Tab</option>
                </select>
                <div class="form-text text-muted">
                  Select header menu layout style
                </div>
              </div>
            </div>

            <div class="form-group row">
              <label class="col-lg-3 col-form-label">
                Header Menu Arrows:
              </label>
              <div class="col-lg-9 col-xl-4">
                <span class="switch switch-icon">
                  <label>
                    <input
                      type="checkbox"
                      v-model="config.header.menu.self['root-arrow']"
                      value="true"
                    />
                    <span></span>
                  </label>
                </span>
                <div class="form-text text-muted">
                  Enable header menu root link arrows
                </div>
              </div>
            </div>
          </b-tab>

          <b-tab>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label">
                Display Subheader:
              </label>
              <div class="col-lg-9 col-xl-4">
                <span class="switch switch-icon">
                  <label>
                    <input
                      type="checkbox"
                      v-model="config.subheader.display"
                      value="true"
                      checked=""
                    />
                    <span></span>
                  </label>
                </span>
                <div class="form-text text-muted">Display subheader</div>
              </div>
            </div>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label"> Fixed Subheader: </label>
              <div class="col-lg-9 col-xl-4">
                <span class="switch switch-icon">
                  <label>
                    <input
                      type="checkbox"
                      v-model="config.subheader.fixed"
                      value="true"
                      checked=""
                    />
                    <span></span>
                  </label>
                </span>
                <div class="form-text text-muted">
                  Enable fixed(sticky) subheader. Requires
                  <code>Solid</code> subheader style.
                </div>
              </div>
            </div>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label">Width:</label>
              <div class="col-lg-9 col-xl-4">
                <select class="form-control" v-model="config.subheader.width">
                  <option value="fluid" selected="">Fluid</option>
                  <option value="fixed">Fixed</option>
                </select>
                <div class="form-text text-muted">
                  Select layout width type.
                </div>
              </div>
            </div>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label">Subheader Style:</label>
              <div class="col-lg-9 col-xl-4">
                <select class="form-control" v-model="config.subheader.style">
                  <option value="transparent">Transparent</option>
                  <option value="solid" selected="">Solid</option>
                </select>
                <div class="form-text text-muted">Select subheader style</div>
              </div>
            </div>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label">Subheader Layout:</label>
              <div class="col-lg-9 col-xl-4">
                <select class="form-control" v-model="config.subheader.layout">
                  <option value="subheader-v1" selected="">Subheader v1</option>
                </select>
                <div class="form-text text-muted">Select subheader layout</div>
              </div>
            </div>
          </b-tab>

          <b-tab>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label">Width:</label>
              <div class="col-lg-9 col-xl-4">
                <select class="form-control" v-model="config.content.width">
                  <option value="fluid">Fluid</option>
                  <option value="fixed" selected="">Fixed</option>
                </select>
                <div class="form-text text-muted">
                  Select layout width type.
                </div>
              </div>
            </div>
          </b-tab>

          <b-tab>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label">Display:</label>
              <div class="col-lg-9 col-xl-4">
                <span class="switch switch-icon">
                  <label>
                    <input
                      type="checkbox"
                      v-model="config.aside.self.display"
                      value="true"
                      checked=""
                    />
                    <span></span>
                  </label>
                </span>
                <div class="form-text text-muted">Display aside</div>
              </div>
            </div>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label">Fixed:</label>
              <div class="col-lg-9 col-xl-4">
                <span class="switch switch-icon">
                  <label>
                    <input
                      type="checkbox"
                      v-model="config.aside.self.fixed"
                      value="true"
                      checked=""
                    />
                    <span></span>
                  </label>
                </span>
                <div class="form-text text-muted">Set fixed aside layout</div>
              </div>
            </div>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label">Minimize:</label>
              <div class="col-lg-9 col-xl-4">
                <span class="switch switch-icon">
                  <label>
                    <input
                      type="checkbox"
                      v-model="config.aside.self.minimize.toggle"
                      value="true"
                      checked=""
                    />
                    <span></span>
                  </label>
                </span>
                <div class="form-text text-muted">Allow aside minimizing</div>
              </div>
            </div>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label"> Default Minimize: </label>
              <div class="col-lg-9 col-xl-4">
                <span class="switch switch-icon">
                  <label>
                    <input
                      type="checkbox"
                      v-model="config.aside.self.minimize.default"
                      value="true"
                    />
                    <span></span>
                  </label>
                </span>
                <div class="form-text text-muted">
                  Set aside minimized by default
                </div>
              </div>
            </div>
          </b-tab>

          <b-tab>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label">Fixed Footer:</label>
              <div class="col-lg-9 col-xl-4">
                <span class="switch switch-icon">
                  <label>
                    <input
                      type="checkbox"
                      v-model="config.footer.fixed"
                      value="true"
                    />
                    <span></span>
                  </label>
                </span>
                <div class="form-text text-muted">Set fixed footer</div>
              </div>
            </div>
            <div class="form-group row">
              <label class="col-lg-3 col-form-label">Width:</label>
              <div class="col-lg-9 col-xl-4">
                <select class="form-control" v-model="config.footer.width">
                  <option value="fluid" selected="">Fluid</option>
                  <option value="fixed">Fixed</option>
                </select>
                <div class="form-text text-muted">
                  Select layout width type.
                </div>
              </div>
            </div>
          </b-tab>
        </b-tabs>
      </div>
      <!--end::Tab Content-->
    </div>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import { SET_BREADCRUMB } from "@/core/services/store/breadcrumbs.module";
import DatePicker from "vue2-datepicker";
import "vue2-datepicker/index.css";

export default {
  name: "sales-order",
  components: { DatePicker },
  data() {
    return {
      tabIndex: 0,
      value1: null,
      chartOptions: {},
      series: [
        {
          name: "Unprocessed",
          data: [40, 40, 30, 30, 35],
        },
      ],
      chartOptions2: {},
      series2: [
        {
          name: "Shipped",
          data: [60, 40, 20, 30, 15],
        },
      ],
      chartOptions3: {},
      series3: [
        {
          name: "Cancelled",
          data: [50, 15, 80, 20, 35],
        },
      ],
      chartOptions4: {},
      series4: [
        {
          name: "Back Ordered",
          data: [45, 20, 10, 40, 75],
        },
      ],
    };
  },
  computed: {
    ...mapGetters(["layoutConfig"]),

    config() {
      return this.layoutConfig();
    },
  },
  mounted() {
    this.chartOptions = {
      chart: {
        type: "bar",
        height: 150,
        toolbar: {
          show: false,
        },
        zoom: {
          enabled: false,
        },
        sparkline: {
          enabled: true,
        },
      },
      plotOptions: {},
      legend: {
        show: false,
      },
      dataLabels: {
        enabled: false,
      },
      fill: {
        type: "solid",
        opacity: 1,
      },
      stroke: {
        curve: "smooth",
        show: true,
        width: 3,
        colors: [this.layoutConfig("colors.theme.light.danger")],
      },
      xaxis: {
        categories: [
          "Wayfair",
          "HomeDepot",
          "Pacific Ham",
          "Others",
          "BigStock",
        ],
        axisBorder: {
          show: false,
        },
        axisTicks: {
          show: false,
        },
        labels: {
          show: false,
          style: {
            colors: this.layoutConfig("colors.gray.gray-500"),
            fontSize: "12px",
            fontFamily: this.layoutConfig("font-family"),
          },
        },
        crosshairs: {
          show: false,
          position: "front",
          stroke: {
            color: this.layoutConfig("colors.gray.gray-300"),
            width: 1,
            dashArray: 3,
          },
        },
        tooltip: {
          enabled: false,
        },
      },
      yaxis: {
        min: 0,
        max: 100,
        show: false,
        labels: {
          show: false,
          style: {
            colors: this.layoutConfig("colors.gray.gray-500"),
            fontSize: "12px",
            fontFamily: this.layoutConfig("font-family"),
          },
        },
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
          formatter: function (val) {
            return "$" + val + " thousands";
          },
        },
      },
      colors: [this.layoutConfig("colors.theme.light.danger")],
      markers: {
        colors: [this.layoutConfig("colors.theme.light.danger")],
        strokeColor: [this.layoutConfig("colors.theme.light.danger")],
        strokeWidth: 3,
      },
      grid: {
        show: false,
        padding: {
          left: 0,
          right: 0,
        },
      },
    };

    this.chartOptions2 = {
      chart: {
        type: "bar",
        height: 150,
        toolbar: {
          show: false,
        },
        zoom: {
          enabled: false,
        },
        sparkline: {
          enabled: true,
        },
      },
      plotOptions: {},
      legend: {
        show: false,
      },
      dataLabels: {
        enabled: false,
      },
      fill: {
        type: "solid",
        opacity: 1,
      },
      stroke: {
        curve: "smooth",
        show: true,
        width: 3,
        colors: [this.layoutConfig("colors.theme.light.info")],
      },
      xaxis: {
        categories: [
          "Wayfair",
          "HomeDepot",
          "Pacific Ham",
          "Others",
          "BigStock",
        ],
        axisBorder: {
          show: false,
        },
        axisTicks: {
          show: false,
        },
        labels: {
          show: false,
          style: {
            colors: this.layoutConfig("colors.gray.gray-500"),
            fontSize: "12px",
            fontFamily: this.layoutConfig("font-family"),
          },
        },
        crosshairs: {
          show: false,
          position: "front",
          stroke: {
            color: this.layoutConfig("colors.gray.gray-300"),
            width: 1,
            dashArray: 3,
          },
        },
        tooltip: {
          enabled: false,
        },
      },
      yaxis: {
        min: 0,
        max: 100,
        show: false,
        labels: {
          show: false,
          style: {
            colors: this.layoutConfig("colors.gray.gray-500"),
            fontSize: "12px",
            fontFamily: this.layoutConfig("font-family"),
          },
        },
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
          formatter: function (val) {
            return "$" + val + " thousands";
          },
        },
      },
      colors: [this.layoutConfig("colors.theme.light.info")],
      markers: {
        colors: [this.layoutConfig("colors.theme.light.info")],
        strokeColor: [this.layoutConfig("colors.theme.light.info")],
        strokeWidth: 3,
      },
      grid: {
        show: false,
        padding: {
          left: 0,
          right: 0,
        },
      },
    };

    this.chartOptions3 = {
      chart: {
        type: "bar",
        height: 150,
        toolbar: {
          show: false,
        },
        zoom: {
          enabled: false,
        },
        sparkline: {
          enabled: true,
        },
      },
      plotOptions: {},
      legend: {
        show: false,
      },
      dataLabels: {
        enabled: false,
      },
      fill: {
        type: "solid",
        opacity: 1,
      },
      stroke: {
        curve: "smooth",
        show: true,
        width: 3,
        colors: [this.layoutConfig("colors.theme.light.success")],
      },
      xaxis: {
        categories: [
          "Wayfair",
          "HomeDepot",
          "Pacific Ham",
          "Others",
          "BigStock",
        ],
        axisBorder: {
          show: false,
        },
        axisTicks: {
          show: false,
        },
        labels: {
          show: false,
          style: {
            colors: this.layoutConfig("colors.gray.gray-500"),
            fontSize: "12px",
            fontFamily: this.layoutConfig("font-family"),
          },
        },
        crosshairs: {
          show: false,
          position: "front",
          stroke: {
            color: this.layoutConfig("colors.gray.gray-300"),
            width: 1,
            dashArray: 3,
          },
        },
        tooltip: {
          enabled: false,
        },
      },
      yaxis: {
        min: 0,
        max: 100,
        show: false,
        labels: {
          show: false,
          style: {
            colors: this.layoutConfig("colors.gray.gray-500"),
            fontSize: "12px",
            fontFamily: this.layoutConfig("font-family"),
          },
        },
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
          formatter: function (val) {
            return "$" + val + " thousands";
          },
        },
      },
      colors: [this.layoutConfig("colors.theme.light.success")],
      markers: {
        colors: [this.layoutConfig("colors.theme.light.success")],
        strokeColor: [this.layoutConfig("colors.theme.light.success")],
        strokeWidth: 3,
      },
      grid: {
        show: false,
        padding: {
          left: 0,
          right: 0,
        },
      },
    };

    this.chartOptions4 = {
      chart: {
        type: "bar",
        height: 150,
        toolbar: {
          show: false,
        },
        zoom: {
          enabled: false,
        },
        sparkline: {
          enabled: true,
        },
      },
      plotOptions: {},
      legend: {
        show: false,
      },
      dataLabels: {
        enabled: false,
      },
      fill: {
        type: "solid",
        opacity: 1,
      },
      stroke: {
        curve: "smooth",
        show: true,
        width: 3,
        colors: [this.layoutConfig("colors.theme.light.warning")],
      },
      xaxis: {
        categories: [
          "Wayfair",
          "HomeDepot",
          "Pacific Ham",
          "Others",
          "BigStock",
        ],
        axisBorder: {
          show: false,
        },
        axisTicks: {
          show: false,
        },
        labels: {
          show: false,
          style: {
            colors: this.layoutConfig("colors.gray.gray-500"),
            fontSize: "12px",
            fontFamily: this.layoutConfig("font-family"),
          },
        },
        crosshairs: {
          show: false,
          position: "front",
          stroke: {
            color: this.layoutConfig("colors.gray.gray-300"),
            width: 1,
            dashArray: 3,
          },
        },
        tooltip: {
          enabled: false,
        },
      },
      yaxis: {
        min: 0,
        max: 100,
        show: false,
        labels: {
          show: false,
          style: {
            colors: this.layoutConfig("colors.gray.gray-500"),
            fontSize: "12px",
            fontFamily: this.layoutConfig("font-family"),
          },
        },
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
          formatter: function (val) {
            return "$" + val + " thousands";
          },
        },
      },
      colors: [this.layoutConfig("colors.theme.light.warning")],
      markers: {
        colors: [this.layoutConfig("colors.theme.light.warning")],
        strokeColor: [this.layoutConfig("colors.theme.light.warning")],
        strokeWidth: 3,
      },
      grid: {
        show: false,
        padding: {
          left: 0,
          right: 0,
        },
      },
    };
    // set the tab from previous
    this.setActivePreviousTab();

    this.$store.dispatch(SET_BREADCRUMB, [{ title: "Sales Order" }]);

    this.$nextTick(() => {
      const hljs = this.$el.querySelectorAll(".hljs");
      hljs.forEach((hl) => {
        hl.classList.remove("hljs");
        hl.classList.add(`language-${hl.classList[1]}`);
      });
    });
  },
  destroyed() {
    localStorage.removeItem("builderTab");
  },
  methods: {
    /**
     * Reset config
     */
    reset(event) {
      event.preventDefault();
      // remove existing saved config
      localStorage.removeItem("config");
      window.location.reload();
    },

    /**
     * Set previous tab active
     */
    setActivePreviousTab() {
      this.tabIndex = parseInt(localStorage.getItem("builderTab")) || 0;
      const links = this.$refs["builder-tab"].querySelectorAll(".nav-link");
      // remove active tab links
      for (let i = 0; i < links.length; i++) {
        links[i].classList.remove("active");
      }
      this.$refs["builder-tab"]
        .querySelector(`[data-tab="${this.tabIndex}"]`)
        .classList.add("active");
    },
    /**
     * Set current active on click
     * @param event
     */
    setActiveTab(event) {
      const tab = event.target.closest('[role="tablist"]');
      const links = tab.querySelectorAll(".nav-link");
      // remove active tab links
      for (let i = 0; i < links.length; i++) {
        links[i].classList.remove("active");
      }

      // set clicked tab index to bootstrap tab
      this.tabIndex = parseInt(event.target.getAttribute("data-tab"));

      // set current active tab
      event.target.classList.add("active");

      // keep active tab
      localStorage.setItem("builderTab", this.tabIndex);
    },

    /**
     * Submit form
     * @param event
     */
    submit(event) {
      event.preventDefault();
      // save new config to localStorage
      localStorage.setItem("config", JSON.stringify(this.config));
      window.location.reload();
    },
  },
};
</script>
