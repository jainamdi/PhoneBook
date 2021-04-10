<template>
  <div class="hello">
    <p><strong> Add a new contact: </strong></p>
    <div>
      <label
        >First Name:
        <input type="text" v-model="first_name" pattern="[a-zA-Z0-9]+"
      /></label>
      <br />
      <label
        >Last Name:
        <input type="text" v-model="last_name" pattern="[a-zA-Z0-9]+" /></label
      ><br />
      <label
        >Phone:
        <input type="number" v-model="contact_number" pattern="[0-9]+" /></label
      ><br />
      <button
        class="submitButton"
        v-on:click="addContact"
        :disabled="
          !last_name.length || !first_name.length || !contact_number.length
        "
      >
        Add new Contact
      </button>
      <table id="phoneBookItems" class="data">
        <tr>
          <th>Firstname</th>
          <th>Lastname</th>
          <th>Phone</th>
        </tr>
        <tr v-for="(contact_detail, index) in items" :key="index">
          <td>{{ contact_detail.first_name }}</td>
          <td>{{ contact_detail.last_name }}</td>
          <td>{{ contact_detail.contact_number }}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      first_name: "Coder",
      last_name: "Byte",
      contact_number: "8885559999",
      items: [],
      flag: true,
    };
  },
  methods: {
    addContact() {
      const contact_details = {
        first_name: this.first_name,
        last_name: this.last_name,
        contact_number: this.contact_number,
      };

      this.items.push(contact_details);
      this.items = this.items.sort((a, b) =>
        a.last_name.toLowerCase() > b.last_name.toLowerCase() ? 1 : -1
      );
      this.first_name = "";
      this.last_name = "";
      this.contact_number = "";
      console.log(this.items);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
label {
  color: black;
  background-color: #e7e7e7;
  margin: 30px;
}
div {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}
input[type="text"],
input[type="number"] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}
button {
  width: 100%;
  background-color: #4CAF50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

.data th {
  padding: 12px;
  text-align: left;
  background-color: #537FD8;
}

.data tr:nth-child(odd) {
  background-color: #DFE3EC;
}

.data tr:nth-child(even) {
  background-color: #93B3FA;
}
</style>
