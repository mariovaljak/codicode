<template>
  <button class="home-btn">Dodaj novu lokaciju</button>
  <SubmitForm />
</template>

<script>
import SubmitForm from "../components/SubmitForm.vue";
export default {
  name: "Home",
  components: {
    SubmitForm,
  },
};
</script>

<style scoped>
.home-btn {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: none;
  border: 2px solid #ffce00;
  padding: 10px 20px;
  font-size: 12px;
  cursor: pointer;
  border-radius: 8px;
  transition: 0.4s;
  text-transform: uppercase;
  font-weight: bold;
  color: #ffce00;
}

.home-btn:hover {
  color: #fff;
  background: #ffce00;
}
</style>
