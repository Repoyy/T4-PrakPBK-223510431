<template>
  <div class="parent">
    <h2 class="header">Komponen Induk</h2>
    <textarea v-model="message" cols="30" rows="10">{{ message }}</textarea>
    <button @click="showChild = true" class="open-modal-button">Buka Komponen Anak</button>
    <Modal v-if="showChild" @close="showChild = false">
      <ChildComponent @childEvent="updateMessage" />
    </Modal>
  </div>
</template>

<script>
import ChildComponent from './ChildComponent.vue';
import Modal from './Modal.vue';

export default {
  name: 'ParentComponent',
  components: {
    ChildComponent,
    Modal,
  },
  data() {
    return {
      message: 'this is a parent component',
      showChild: false,
    };
  },
  methods: {
    updateMessage(newMessage) {
      this.message = newMessage;
    },
  },
};
</script>

<style scoped>
.parent {
  padding: 20px;
  border: 2px solid #76b39d;
  border-radius: 10px;
  margin-top: 15px;
  background-color: #b3e5dc;
  transition: all 0.3s ease;
}

.parent:hover {
  background-color: #a8d5c9;
}

textarea {
  width: 97%;
  padding: 10px;
  font-family: 'Helvetica Neue', Arial, sans-serif;
  font-size: 18px;
  border: 2px solid #76b39d;
  border-radius: 5px;
  resize: vertical;
  margin-bottom: 10px;
  text-align: center;
  background-color: #dcedc1;
  color: #333;
  height: 100px;
}

.header {
  font-size: 22px;
}

.open-modal-button {
  padding: 10px 20px;
  background-color: #76b39d;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  margin-top: 10px;
}

.open-modal-button:hover {
  background-color: #5b9980;
}
</style>
