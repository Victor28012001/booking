<template>
  <div v-if="isOpen" class="modal">
    <div class="modal-content">
      <h2>Rate Your Booking</h2>
      <p>Booking ID: {{ bookingId }}</p>
      <div class="stars">
        <span
          v-for="star in 5"
          :key="star"
          class="star"
          :class="{ 'filled': star <= rating }"
          @click="rate(star)"
        >
          ★
        </span>
      </div>
      <textarea v-model="feedback" placeholder="Leave your feedback" required></textarea>
      <button @click="submitRating">Submit Rating</button>
      <button @click="closeRatingModal">Close</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false,
      bookingId: null,
      rating: 0,
      feedback: '',
    };
  },
  methods: {
    openRatingModal(bookingId) {
      // Open modal and set booking ID
      this.bookingId = bookingId;
      this.isOpen = true;
    },
    closeRatingModal() {
      this.isOpen = false;
    },
    rate(star) {
      this.rating = star;
    },
    submitRating() {
      console.log('Rating Submitted for Booking ID:', this.bookingId, 'Rating:', this.rating, 'Feedback:', this.feedback);
    },
  },
};
</script>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  background-color: white;
  padding: 20px;
  border-radius: 8px;
  width: 400px;
}

.stars {
  display: flex;
  justify-content: center;
}

.star {
  font-size: 2rem;
  cursor: pointer;
}

.star.filled {
  color: gold;
}

textarea {
  width: 100%;
  height: 100px;
  margin-top: 10px;
}

button {
  width: 100%;
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  margin-top: 10px;
}

button:hover {
  background-color: #0056b3;
}
</style>
