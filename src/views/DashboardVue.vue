<template>
  <v-sheet
    max-width="1550px"
    color="#EFEFEF"
    class="mx-auto"
  >
    <v-container
      fluid
      class="px-0"
    >
      <v-row class="my-4 mx-4 justify-space-between align center">
        <p class="my-2 text-subtitle-1 font-weight-bold">
          No. of Staffs:
          <v-chip
            class="ma-1 deep-purple lighten-3 white--text"
            label
          >
            {{ totalStaffs }}
          </v-chip>
        </p>
        <div class="d-flex">
          <v-btn
            class="mr-4 mt-4 mb-8"
            color="deep-purple lighten-3"
            outlined
            x-large
            to="/create/employee"
          >
            Add Staff
          </v-btn>
        </div>
      </v-row>
      <StaffsTable :staffs="employees" />
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
      linkItems: [{ title: "Employee", link: "/create/employee" }],
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