<template>
  <!--begin::Advance Table Widget 9-->
  <div class="card card-custom card-stretch gutter-b">
    <!--begin::Header
    <div class="card-header border-0 py-5">
      <h3 class="card-title align-items-start flex-column">
        <span class="card-label font-weight-bolder text-dark"
          >Agents Stats</span
        >
        <span class="text-muted mt-3 font-weight-bold font-size-sm"
          >More than 400+ new members</span
        >
      </h3>
      <div class="card-toolbar">
        <a class="btn btn-info font-weight-bolder font-size-sm mr-3"
          >New Arrivals</a
        >
        <a class="btn btn-danger font-weight-bolder font-size-sm">Create</a>
      </div>
    </div>
    end::Header-->
    <!--begin::Body-->
    <div class="card-body pt-0 pb-3 pt-5">
      <div class="tab-content">
        <!--begin::Table-->
        <div class="table-responsive">
          <table
            class="table table-head-custom table-vertical-center table-head-bg table-borderless"
          >
            <thead>
              <tr class="text-left">
                <th style="min-width: 250px" class="pl-7">
                  <span class="text-dark-75">Customer</span>
                </th>
                <th style="min-width: 120px">Revenue</th>
                <th style="min-width: 100px">Comission</th>
                <th style="min-width: 100px">Company</th>
                <th style="min-width: 100px">Sales</th>
              </tr>
            </thead>
            <tbody>
              <template v-for="(item, i) in list">
                <tr v-bind:key="i">
                  <td class="pl-0 pt-8">
                    <div class="d-flex align-items-center">
                      <div class="symbol symbol-50 symbol-light mr-4">
                        <span class="symbol-label">
                          <img
                            :src="item.img"
                            class="h-75 align-self-end"
                            alt=""
                          />
                        </span>
                      </div>
                      <div>
                        <a
                          class="text-dark-75 font-weight-bolder text-hover-primary mb-1 font-size-lg"
                          >{{ item.name }}</a
                        >
                        <span class="text-muted font-weight-bold d-block">{{
                          item.desc
                        }}</span>
                      </div>
                    </div>
                  </td>
                  <td>
                    <span
                      class="text-dark-75 font-weight-bolder d-block font-size-lg"
                      >{{ item.paid }}</span
                    >
                    <span class="text-muted font-weight-bold">{{
                      item.status
                    }}</span>
                  </td>
                  <td>
                    <span
                      class="text-dark-75 font-weight-bolder d-block font-size-lg"
                      >{{ item.amount }}</span
                    >
                    <span class="text-muted font-weight-bold">{{
                      item.status2
                    }}</span>
                  </td>
                  <td>
                    <span
                      class="text-dark-75 font-weight-bolder d-block font-size-lg"
                      >{{ item.company }}</span
                    >
                    <span class="text-muted font-weight-bold">{{
                      item.company_desc
                    }}</span>
                  </td>
                  <td class="d-flex align-items-center mt-6">
                    <span class="text-muted font-weight-bold d-block my-auto mr-5"
                    >{{item.rate}}%</span
                    >
                    <img
                      class="my-auto"
                      :src="item.sales"
                      alt="image"
                      style="width: 2rem"
                    />
                  </td>
                </tr>
              </template>
            </tbody>
          </table>
        </div>
        <!--end::Table-->
      </div>
    </div>
    <!--end::Body-->
  </div>
  <!--end::Advance Table Widget 9-->
</template>

<script>
export default {
  name: "widget-3",
  data() {
    return {
      list: [
        {
          img: "media/svg/avatars/001-boy.svg",
          name: "Brad Simmons",
          desc: "bradsim@intertico.com",
          paid: "$8,000,000",
          status: "In Proccess",
          status2: "Paid",
          amount: "$520",
          company: "Intertico",
          company_desc: "Web, UI/UX Design",
          rate: "68",
          sales: "media/svg/icons/Shopping/Chart-down.svg"
        },
        {
          img: "media/svg/avatars/018-girl-9.svg",
          name: "Jessie Clarcson",
          desc: "jess@agoda.com",
          paid: "$23,000,000",
          status: "Pending",
          status2: "Rejected",
          amount: "$1,600",
          company: "Agoda",
          company_desc: "Houses & Hotels",
          rate: "97",
          sales: "media/svg/icons/Shopping/Chart-down.svg"
        },
        {
          img: "media/svg/avatars/014-girl-7.svg",
          name: "Lebron Wayde",
          desc: "lebronw@roadgee.com",
          paid: "$2,600,000",
          status: "Paid",
          status2: "Paid",
          amount: "$6,700",
          company: "RoadGee",
          company_desc: "Transportation",
          rate: "62",
          sales: "media/svg/icons/Shopping/Chart-up.svg"
        },
        {
          img: "media/svg/avatars/047-girl-25.svg",
          name: "Natali Trump",
          desc: "trumpnat@hill.com",
          paid: "$2,600,000",
          status: "Paid",
          status2: "Pending",
          amount: "$14,000",
          company: "The Hill",
          company_desc: "Insurance",
          rate: "78",
          sales: "media/svg/icons/Shopping/Chart-up.svg"
        }
      ]
    };
  }
};
</script>
