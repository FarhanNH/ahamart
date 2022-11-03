<template>
  <div>
    <v-layout row>
      <v-flex md12>
        <v-btn dark depressed small color="#50CD89">Tambah Outlet</v-btn>
      </v-flex>
    </v-layout>
    <v-layout row class="pt-4" id="topContent">
      <v-flex class="mr-4">
        <v-card class="content-1">
          <v-card-title class="font-weight-bold"> Jumlah Outlet </v-card-title>
          <v-divider></v-divider>
          <div class="d-flex justify-space-between my-2">
            <div class="d-flex align-center ml-4">
              <h1>73</h1>
              <v-chip
                class="ma-2"
                color="#E8FFF3"
                text-color="#2BA579"
                small
                label
              >
                +2 Toko
              </v-chip>
            </div>
            <div>
              <v-btn-toggle v-model="periode" tile group color="#0095E8">
                <v-btn value="Week"> Week </v-btn>
                <v-btn value="Month"> Month </v-btn>
                <v-btn value="Year"> Year </v-btn>
              </v-btn-toggle>
            </div>
          </div>
          <div class="d-flex justify-end">
            <div style="width: 20%" class="mr-4">
              <v-select
                :items="yearsOption"
                v-model="year"
                dense
                outlined
              ></v-select>
            </div>
          </div>
          <v-sheet class="stackSheet" color="white">
            <v-sparkline
              :value="value1"
              :gradient="gradient1"
              line-width="5"
              smooth="5"
              padding="5"
              type="bar"
              :show-labels="true"
              :labels="labels"
            ></v-sparkline>
            <!-- <v-sparkline class="stackSpark" :value="value2" :gradient="gradient2" line-width="3" padding="5" type="bar"></v-sparkline> -->
          </v-sheet>
          <!-- <v-sparkline
              :value="dataGraph"
              :gradient="gradient"
              :smooth="radius || false"
              :line-width="width"
              :stroke-linecap="lineCap"
              :gradient-direction="gradientDirection"
              :fill="fill"
              :type="type"
              :auto-line-width="autoLineWidth"
              auto-draw
              :show-labels="true"
              :labels="labels"
            >
            </v-sparkline> -->
        </v-card>
      </v-flex>
      <v-flex md3 class="mr-4">
        <v-card class="content-2">
          <v-card-title class="font-weight-bold">
            Outlet Terlaris
          </v-card-title>
          <v-divider></v-divider>
          <div class="container-mytable">
            <table class="mytable">
              <thead>
                <tr>
                  <th class="text-left">Nama Outlet</th>
                  <th class="text-right">Pendapatan</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="item in outletTerlaris" :key="item.id">
                  <td class="d-flex flex-column">
                    <label class="font-weight-bold">
                      {{ item.outletName }}
                    </label>
                    <label class="caption">
                      {{ item.location }}
                    </label>
                  </td>
                  <td class="text-right">
                    <v-btn disabled>
                      {{ item.income }}
                    </v-btn>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </v-card>
      </v-flex>
      <v-flex md3 class="mr-4">
        <v-card class="content-3">
          <v-card-title class="font-weight-bold"> Outlet Baru </v-card-title>
          <v-divider></v-divider>
          <div class="container-mytable">
            <table class="mytable">
              <thead>
                <tr>
                  <th class="text-left">Nama Outlet</th>
                  <th class="text-right">Tanggal Daftar</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="item in outletBaru" :key="item.id">
                  <td class="d-flex flex-column">
                    <label class="font-weight-bold">
                      {{ item.outletName }}
                    </label>
                    <label class="caption">
                      {{ item.location }}
                    </label>
                  </td>
                  <td class="text-right">
                    <v-btn disabled>
                      {{ item.joinDate }}
                    </v-btn>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </v-card>
      </v-flex>
    </v-layout>
    <v-layout row class="pt-4">
      <v-flex md12 class="mr-4">
        <v-card>
          <v-card-title class="font-weight-bold"> List Outlet </v-card-title>
          <v-divider></v-divider>
          <div class="d-flex justify-space-between mt-4 mx-4">
            <div>
              <v-select
                :items="locationOption"
                v-model="location"
                dense
                outlined
              ></v-select>
            </div>
            <div>
              <v-text-field
                label="Search"
                prepend-inner-icon="mdi-magnify"
                outlined
                dense
              ></v-text-field>
            </div>
          </div>
          <div class="pb-4">
            <v-data-table
              hide-default-header
              hide-default-footer
              :items="outletList"
              :headers="headersTable"
              @page-count="pageCount = $event"
              no-data-text="Data Tidak Ditemukan"
            >
              <template #header="{ props: { headers } }">
                <thead class="v-data-table-header">
                  <tr>
                    <th
                      v-for="header in headers"
                      :key="header.value"
                      class="#7e8299"
                    >
                      {{ header.text }}
                    </th>
                  </tr>
                </thead>
              </template>
              <template #[`item.action`]="{ item }">
                <v-btn v-if="item != null" depressed dark small color="#0095E8">
                  Rincian
                </v-btn>
              </template>
            </v-data-table>
          </div>
        </v-card>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
export default {
  outletName: "Content",

  data: () => ({
    value1: [5, 2, 5, 9, 5, 15, 3, 5, 5, 5, 1, 8],
    value2: [7, 4, 7, 2, 9, 5, 1, 2, 4, 7, 7, 10],
    gradient1: ["#00A3FF"],
    gradient2: ["#EFF2F5"],
    labels: [
      "Jan",
      "Feb",
      "Mar",
      "Apr",
      "Mei",
      "Jun",
      "Jul",
      "Aug",
      "Sep",
      "Oct",
      "Nov",
      "Dec",
    ],
    dataGraph: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12],
    outletTerlaris: [
      {
        id: 1,
        outletName: "Toko ABC",
        location: "Bandung",
        income: "Rp. 20.000.000",
      },
      {
        id: 2,
        outletName: "Toko ABC",
        location: "Jakarta",
        income: "Rp. 17.000.000",
      },
      {
        id: 3,
        outletName: "Toko ABC",
        location: "Solo",
        income: "Rp. 12.500.000",
      },
      {
        id: 4,
        outletName: "Toko ABC",
        location: "Semarang",
        income: "Rp. 11.500.000",
      },
      {
        id: 5,
        outletName: "Toko ABC",
        location: "Bandung",
        income: "Rp. 10.000.000",
      },
      {
        id: 6,
        outletName: "Toko ABC",
        location: "Bandung",
        income: "Rp. 9.000.000",
      },
    ],
    outletBaru: [
      {
        id: 1,
        outletName: "Toko ABC",
        location: "Bandung",
        joinDate: "2 Juni 2022",
      },
      {
        id: 2,
        outletName: "Toko ABC",
        location: "Jakarta",
        joinDate: "2 Juni 2022",
      },
      {
        id: 3,
        outletName: "Toko ABC",
        location: "Solo",
        joinDate: "2 Juni 2022",
      },
      {
        id: 4,
        outletName: "Toko ABC",
        location: "Semarang",
        joinDate: "2 Juni 2022",
      },
      {
        id: 5,
        outletName: "Toko ABC",
        location: "Bandung",
        joinDate: "2 Juni 2022",
      },
      {
        id: 6,
        outletName: "Toko ABC",
        location: "Bandung",
        joinDate: "2 Juni 2022",
      },
    ],
    headersTable: [
      {
        text: "No",
        value: "no",
      },
      {
        text: "Nama Outlet",
        value: "outletName",
      },
      {
        text: "Nama Pemilik",
        value: "owner",
      },
      {
        text: "Jumlah Transaksi",
        value: "totalTransaction",
      },
      {
        text: "Lokasi",
        value: "location",
      },
      {
        text: "Tanggal Daftar",
        value: "joinDate",
      },
      {
        text: "Pendapatan",
        value: "income",
      },
      {
        text: "Action",
        value: "action",
      },
    ],
    outletData: "",
    outletList: [
      {
        no: 1,
        outletName: "Toko 1",
        owner: "Floyd Miles",
        totalTransaction: 23,
        location: "Bandung",
        joinDate: "2 Juni 2022",
        income: "Rp. 20.000.000",
        action: true,
      },
      {
        no: 2,
        outletName: "Toko 2",
        owner: "Robert Fox",
        totalTransaction: 12,
        location: "Jakarta",
        joinDate: "2 Juni 2022",
        income: "Rp. 20.000.000",
        action: true,
      },
      {
        no: 3,
        outletName: "Toko 3",
        owner: "Courtney Henry",
        totalTransaction: 31,
        location: "Solo",
        joinDate: "2 Juni 2022",
        income: "Rp. 20.000.000",
        action: true,
      },
      {
        no: 4,
        outletName: "Toko 4",
        owner: "Arlene McCoy",
        totalTransaction: 23,
        location: "Semarang",
        joinDate: "2 Juni 2022",
        income: "Rp. 20.000.000",
        action: true,
      },
      {
        no: 5,
        outletName: "Toko 5",
        owner: "Annette Black",
        totalTransaction: 23,
        location: "Bandung",
        joinDate: "2 Juni 2022",
        income: "Rp. 20.000.000",
        action: true,
      },
    ],
    location: "",
    locationOption: [
      {
        text: "Semua Lokasi",
        value: "",
      },
      {
        text: "Bandung",
        value: "Bandung",
      },
      {
        text: "Jakarta",
        value: "Jakarta",
      },
      {
        text: "Solo",
        value: "Solo",
      },
      {
        text: "Semarang",
        value: "Semarang",
      },
    ],
    year: 2022,
    yearsOption: [2020, 2021, 2022],
    periode: "Month",
  }),
};
</script>
<style lang="css" scoped>
.container-mytable {
  height: 83%;
}
.mytable {
  width: 100%;
  height: 100%;
  padding: 0.5rem 0.75rem;
}
.mytable thead {
  font-size: 0.75rem;
  color: #7e8299;
}
.mytable tr td .font-weight-bold {
  font-size: 1rem;
}
.mytable tr td .caption {
  color: #b5b5c3;
}
.mytable .theme--light.v-btn.v-btn--disabled {
  color: #a1a5b7 !important;
  font-family: "Roboto";
  font-weight: 700;
  font-size: 0.75rem;
}
.stackSheet {
  position: relative;
  /* width: 50%; */
  /* top: 100%;
  transform: translateY(-225%); */
}
.stackSpark {
  position: absolute;
  top: 0;
  left: 20px;
}
#topContent {
  height: auto;
  position: relative;
  overflow: auto;
}
.content-1 {
  height: 100%;
}
.content-2 {
  height: 100%;
}
.content-3 {
  height: 100%;
}
.theme--light.v-btn.v-btn--disabled.v-btn--has-bg {
  background-color: #f5f8fa !important;
}
.theme--light.v-btn.v-btn--disabled {
  color: #a1a5b7 !important;
}
</style>
