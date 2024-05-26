<template>
  <div class="child">
    <div class="child-content">
      <h2 class="child-title">Child Component</h2>
      <div class="input-section">
        <textarea v-model="message" class="message-input" cols="30" rows="10"></textarea>
        <button @click="showGrandchild = true" class="open-modal-button">Open Grandchild Component</button>
        <button @click="sendMessageToParent" class="send-message-button">Send Message to Parent</button>
      </div>
    </div>
    <Modal v-if="showGrandchild" @close="showGrandchild = false">
      <GrandchildComponent @grandchildEvent="handleGrandchildEvent" />
    </Modal>
  </div>
</template>

<script>
import GrandchildComponent from './GrandchildComponent.vue';
import Modal from './Modal.vue';

export default {
  name: 'ChildComponent',
  components: {
    GrandchildComponent,
    Modal,
  },
  data() {
    return {
      showGrandchild: false,
      message: 'This is the Child Component',
    };
  },
  methods: {
    sendMessageToParent() {
      this.$emit('childEvent', this.message);
      console.log('Message sent to parent:', this.message);
    },
    handleGrandchildEvent(message) {
      this.message = message;
      this.$emit('childEvent', message);
      console.log('Message received from grandchild:', message);
    },
  },
};
</script>

<style scoped>
.child {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  border: 2px solid #4f86c6;
  border-radius: 15px;
  margin-top: 15px;
  background-color: #c4d4f2;
  transition: all 0.3s ease;
  font-size: 18px;
  max-width: 500px;
  margin: 0 auto;
}

.child-title {
  color: #4f86c6;
  font-size: 24px;
  margin-bottom: 15px;
}

.child-content {
  text-align: center;
}

.input-section {
  margin-bottom: 20px;
}

.message-input {
  width: 100%;
  padding: 10px;
  font-family: 'Arial', sans-serif;
  font-size: 16px;
  border: 2px solid #4f86c6;
  border-radius: 10px;
  resize: vertical;
  margin-bottom: 10px;
  background-color: #e5ecff;
  color: #333;
}

.open-modal-button,
.send-message-button {
  padding: 10px 20px;
  background-color: #4f86c6;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  margin: 0 10px;
}

.open-modal-button:hover,
.send-message-button:hover {
  background-color: #326aa5;
}

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal {
  background: #ffffff;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
  width: 80%;
  max-width: 600px;
  text-align: center;
}

.close-button {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 5px 10px;
  background-color: #4f86c6;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.close-button:hover {
  background-color: #326aa5;
}
</style>
