<script setup>
import { ref } from "vue";

const STORAGE_KEY = "ogis-v1-notice-dismissed";

const isDismissed = ref(
  typeof localStorage !== "undefined" &&
    localStorage.getItem(STORAGE_KEY) === "true",
);

const dismiss = () => {
  isDismissed.value = true;
  localStorage.setItem(STORAGE_KEY, "true");
};
</script>

<template>
  <aside v-if="!isDismissed" class="retirement-notice">
    <p>
      OGIS v1 has retired — visit the new app at
      <a href="https://ogis.app" target="_blank" rel="noopener">ogis.app</a>
    </p>
    <button
      type="button"
      aria-label="Dismiss retirement notice"
      @click="dismiss"
    >
      ×
    </button>
  </aside>
</template>

<style lang="less" scoped>
.retirement-notice {
  position: absolute;
  top: 0;
  left: 0;
  right: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 6px 40px;
  background-color: #b42714;
  color: white;
  font-family: "Open Sans", sans-serif;
  font-size: 13px;
  line-height: 1.3;
  text-align: center;

  p {
    margin: 0;
  }

  a {
    color: white;
    font-weight: bold;
    text-decoration: underline;
  }

  button {
    position: absolute;
    right: 8px;
    top: 50%;
    transform: translateY(-50%);
    display: flex;
    align-items: center;
    justify-content: center;
    width: 24px;
    height: 24px;
    padding: 0;
    background: transparent;
    border: none;
    color: white;
    font-size: 18px;
    line-height: 1;
    cursor: pointer;
    border-radius: 4px;

    &:hover {
      background-color: rgba(255, 255, 255, 0.2);
    }
  }
}
</style>
