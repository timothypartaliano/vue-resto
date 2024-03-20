<template>
  <div class="container">
    <h2>Reservation Form</h2>
    <form @submit.prevent="submitForm">
      <label for="name">Name:</label>
      <input type="text" id="name" v-model="formData.name" required>

      <label for="email">Email:</label>
      <input type="email" id="email" v-model="formData.email" required>

      <label for="datetime">Date & Time:</label>
      <input type="datetime-local" id="datetime" v-model="formData.datetime" required>

      <label for="people">Number of People:</label>
      <input type="number" id="people" v-model="formData.people" min="1" required>

      <label for="request">Special Request:</label>
      <textarea id="request" v-model="formData.request" rows="4"></textarea>

      <input type="submit" value="Submit">
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        name: '',
        email: '',
        datetime: '',
        people: 1,
        request: ''
      },
      submitted: false
    };
  },
  methods: {
    async submitForm() {
      try {
        const response = await fetch('http://localhost:3000/bookings', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify(this.formData)
        });

        if (response.ok) {
          this.showPopup('Reservation submitted successfully');
          this.resetForm();
        } else {
          console.error('Failed to submit reservation:', response.statusText);
          this.showPopup('Failed to submit reservation');
        }
      } catch (error) {
        console.error('Error submitting reservation:', error);
        this.showPopup('Failed to submit reservation');
      }
    },
    showPopup(message) {
      alert(message);
    },
    resetForm() {
      this.formData = {
        name: '',
        email: '',
        datetime: '',
        people: 1,
        request: ''
      };
    }
  }
};
</script>

<style>
.container {
  background-color: #35495e;
  padding: 40px 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-top: 70px;
}

h2 {
  text-align: center;
  margin-bottom: 30px;
}

label {
  display: block;
  margin-bottom: 8px;
}

input[type="text"],
input[type="email"],
input[type="datetime-local"],
input[type="number"],
textarea {
  width: 100%;
  padding: 10px;
  margin-bottom: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-sizing: border-box;
}

textarea {
  resize: vertical;
}

input[type="submit"] {
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 12px 20px;
  cursor: pointer;
  width: 100%;
  font-size: 16px;
}

input[type="submit"]:hover {
  background-color: #0056b3;
}
</style>