<template>
  <v-sheet max-width="1550px" color="#EFEFEF" class="mx-auto">
    <v-container fluid class="px-0">
      <v-row class="my-4 mx-4 justify-space-between align center">
        <p class="my-2 text-subtitle-1 font-weight-bold">
          No. of Staffs:
          <v-chip class="ma-1 deep-purple lighten-3 white--text" label> {{ totalStaffs }} </v-chip>
        </p>
        <div class="d-flex">
          <v-menu offset-y>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                color="deep-purple lighten-3"
                outlined
                large
                v-bind="attrs"
                v-on="on"
              >
                ADD STAFF
              </v-btn>
            </template>
            <v-list>
              <v-list-item
                v-for="item in linkItems"
                :key="item.title"
                router
                :to="item.link"
              >
                <v-list-item-title v-text="item.title"></v-list-item-title>
              </v-list-item> </v-list
          ></v-menu>
        </div>
      </v-row>
      <StaffsTable :staffs="admins" />
    </v-container>
  </v-sheet>
</template>

<script>
import { mapGetters } from "vuex";
import StaffsTable from "@/components/StaffsTable.vue";

export default {
  name: "Dashboard",
  data() {
    return {
      items: ["admin", "employee"],
      linkItems: [
        { title: "Admin", link: "/create/admin" },
      ],
    };
  },
  computed: {
    ...mapGetters({
      employees: "getEmployees",
      admins: "getAdmins",
      totalStaffs: "getStaffCount",
    }),
  },
  components: { StaffsTable },
};
</script>
