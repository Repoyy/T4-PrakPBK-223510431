<template>
  <div class="grandchild">
    <h2>Komponen Cucu</h2>
    <textarea v-model="message" cols="30" rows="10"></textarea>
    <button @click="sendMessageToChild" class="send-message-button">Kirim Pesan ke Anak</button>
  </div>
</template>

<script>
export default {
  name: 'GrandchildComponent',
  data() {
    return {
      message: 'Ini adalah Komponen Cucu',
    };
  },
  methods: {
    sendMessageToChild() {
      // Mengirim pesan ke komponen induk (ChildComponent)
      this.$emit('grandchildEvent', this.message);
      // Menampilkan pesan di console
      console.log('Pesan yang dikirim dari cucu ke anak:', this.message);
    },
  },
};
</script>

<style scoped>
.grandchild {
  padding: 20px;
  border: 2px solid #76b39d;
  border-radius: 10px;
  margin-top: 15px;
  background-color: #b3e5dc;
  transition: all 0.3s ease;
}

.grandchild:hover {
  background-color: #a8d5c9;
}

button {
  padding: 10px 20px;
  background-color: #76b39d;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #5b9980;
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

h2 {
  font-size: 22px;
}
</style>
