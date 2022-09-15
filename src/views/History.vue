<template>
  <div class="saved-info">
    <table class="content-table">
      <thead>
        <tr>
          <th>Lat</th>
          <th>Lng</th>
          <th>Address</th>
          <th>house_number</th>
          <th>post_code</th>
          <th>city</th>
          <th>country</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="location in locations" :key="location.id">
          <td>
            {{ location.attributes.lat }}
          </td>
          <td>
            {{ location.attributes.lng }}
          </td>
          <td>
            {{ location.attributes.address }}
          </td>
          <td>
            {{ location.attributes.house_number }}
          </td>
          <td>
            {{ location.attributes.post_code }}
          </td>
          <td>
            {{ location.attributes.city }}
          </td>
          <td>
            {{ location.attributes.country
            }}<span @click="deleteTableRow(index)">x</span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "History",

  data() {
    return {
      locations: [],
    };
  },
  async mounted() {
    try {
      const response = await axios.get("http://localhost:1337/api/locations");
      this.locations = response.data.data;
    } catch (error) {
      this.error = error;
    }
  },
  methods: {
    deleteTableRow: function (index) {
      this.locations.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.saved-info {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.content-table {
  background: #fff;
  color: black;
  border-collapse: collapse;
  font-size: 0.9em;
  text-transform: capitalize;
  min-width: 500px;
}

.content-table thead tr {
  background-color: #947490;
  color: white;
  text-align: left;
  text-transform: uppercase;
  font-weight: bold;
}

.content-table th,
td {
  padding: 10px 15px;
}

.content-table tbody tr {
  border-bottom: 2px solid rgb(173, 155, 155);
}

span {
  position: absolute;
  right: 0;
  cursor: pointer;
  width: 15px;
  text-align: center;
  background: #e00;
}
</style>

