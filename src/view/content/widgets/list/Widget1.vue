<template>
  <!--begin::List Widget 1-->
  <div class="card card-custom card-stretch gutter-b">
    <!--begin::Header-->
    <div class="card-header border-0">
      <h3 class="card-title font-weight-bolder text-dark">
        Product Performance
      </h3>
      <div class="card-toolbar">
        <Dropdown3></Dropdown3>
      </div>
    </div>
    <!--end::Header-->
    <!--begin::Body-->
    <div class="card-body pt-2">
      <template v-for="(item, i) in list">
        <!--begin::Item-->
        <div
          class="d-flex align-items-center justify-content-between flex-grow mb-10"
          v-bind:key="i"
        >
          <!--begin::Symbol-->
          <div class="d-flex">
            <div
              class="symbol symbol-40 mr-5"
              v-bind:class="`symbol-light-${item.style}`"
            >
              <span class="symbol-label">
                <span
                  class="svg-icon svg-icon-lg"
                  v-bind:class="`svg-icon-${item.style}`"
                >
                  <!--begin::Svg Icon-->
                  <inline-svg :src="item.svg"></inline-svg>
                  <!--end::Svg Icon-->
                </span>
              </span>
            </div>
            <!--end::Symbol-->
            <!--begin::Text-->
            <div class="d-flex flex-column font-weight-bold">
              <a class="text-dark text-hover-primary mb-1 font-size-lg">
                {{ item.title }}
              </a>
              <span class="text-muted">
                {{ item.desc }}
              </span>
            </div>
          </div>
          <!--end::Text-->
          <!--begin:text-right-->
          <div class="d-flex flex-column text-right">
            <p 
            class="font-weight-bolder my-auto" 
            v-bind:class="`${item.profit}`"
            >
              ${{ item.amount }}
            </p>
          </div>
          <!--end:text-right-->
        </div>
        <!--end::Item-->
      </template>
    </div>
    <!--end::Body-->
  </div>
  <!--end: List Widget 1-->
</template>

<script>
import Dropdown3 from "@/view/content/dropdown/Dropdown3.vue";
import { mapGetters } from "vuex";

export default {
  name: "widget-1",
  data() {
    return {
      list: [
        {
          title: "Company 1",
          desc: "SKU1",
          svg: "media/svg/icons/Home/Library.svg",
          style: "primary",
          amount: "-74",
          profit: "false"
        },
        {
          title: "Company 2",
          desc: "SKU2",
          svg: "media/svg/icons/Communication/Write.svg",
          style: "warning",
          amount: "+480",
          profit: "true"
        },
        {
          title: "Company 3",
          desc: "SKU3",
          svg: "media/svg/icons/Communication/Group-chat.svg",
          style: "success",
          amount: "+590",
          profit: "true"
        },
        {
          title: "Company 4",
          desc: "SKU4",
          svg: "media/svg/icons/General/Attachment2.svg",
          style: "danger",
          amount: "-23",
          profit: "false"
        },
        {
          title: "Company 5",
          desc: "SKU5",
          svg: "media/svg/icons/Communication/Shield-user.svg",
          style: "info",
          amount: "+89",
          profit: "true"
        }
      ]
    };
  },
  components: {
    Dropdown3
  },
  computed: {
    ...mapGetters(["layoutConfig"])
  }
};
</script>
