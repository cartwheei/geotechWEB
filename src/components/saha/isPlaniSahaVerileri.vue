<template>
  <tr class="table--row">
    <td class="table--data">
      {{ item.il_kodu }}
    </td>
    <td class="table--data">
      {{ item.personel_sayı }}
    </td>
    <td class="table--data">
      {{ item.hamveri }}
    </td>
    <td class="table--data">
      {{ item.supurme }}
    </td>
    <td class="table--data">
      {{ item.toplam_is }}
    </td>

    <td class="table--data col align-self-end">
      <button class="btn btn-danger" v-on:click="removeItem()">Sil</button>
      <!-- <button class="btn btn-primary">Güncelle</button> -->
    </td>
  </tr>
</template>

<script>
import axios from "axios";

export default {
  props: ["item"],
  data() {
    return {};
  },
  methods: {
    removeItem() {
      const header = {
        "Content-Type": "application/json;charset=UTF-8",
      };

      var obj = { il_kodu: this.item.il_kodu };

      console.log(obj);
      axios
        .post("http://localhost:2022/sahadel", obj, { headers: header })
        .then((response) => {
          this.$emit("rmValueSaha", obj);
          console.log(response);
        })
        .catch((error) => {
          if (error.response) {
            console.log(error.response, "error response");
            alert(error.response.data.results);
          }
        });
    },
  },
};
</script>