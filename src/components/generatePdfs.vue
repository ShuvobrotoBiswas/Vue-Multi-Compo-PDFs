<template>
  <div id="app">
    <header>
      <h1>Make Invoices</h1>
    </header>

    <main>
      <form @submit.prevent="submitForm">
        <div class="form-group">
          <label for="invoiceNumber">Invoice Number:</label>
          <input
            type="text"
            id="invoiceNumber"
            v-model="invoiceNumber"
            required
          />
        </div>
        <div class="form-group">
          <label for="customerName">Customer Name:</label>
          <input
            type="text"
            id="customerName"
            v-model="customerName"
            required
          />
        </div>
        <button type="submit">Submit</button>
        <button @click="exportToPDF">Generate PDF</button>
      </form>
    </main>
  </div>
</template>

<script>
import html2pdf from "html2pdf.js";

export default {
  name: "App",
  data() {
    return {
      invoiceNumber: "",
      customerName: "",
    };
  },
  methods: {
    submitForm() {
      alert("Form submitted! Downloading PDF...");
      this.exportToPDF();
    },

    exportToPDF() {
      html2pdf().from(document.getElementById("app")).save();
    },
  },
};
</script>

<style scoped>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  padding: 20px;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form-group {
  margin-bottom: 15px;
}

label {
  font-weight: bold;
}

input[type="text"] {
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 250px;
}

button {
  margin-top: 10px;
  padding: 8px 20px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>
