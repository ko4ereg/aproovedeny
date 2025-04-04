<script setup>
import { onMounted, ref } from "vue";

const aproove = ref({
  title: "",
});

const time = ref(5);

const timer = () => {
  if (time.value > 0) {
    time.value--;
  } else {
    clearInterval(timerId.value);
  }
};

const timerId = ref(null);

onMounted(() => {
  timerId.value = setInterval(timer, 1000);
});
</script>

<template>
  <div class="content">
    <div class="title">{{ aproove.title || "Займер" }}</div>
    <div class="divider"></div>
    <div class="logo">
      <v-img
        width="100%"
        aspect-ratio="2/1"
        contain
        src="@/assets/logo.png"
      ></v-img>
    </div>
    <div class="snackbar">
      <div class="icon">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="22"
          height="22"
          viewBox="0 0 22 22"
          fill="none"
        >
          <path
            fill-rule="evenodd"
            clip-rule="evenodd"
            d="M19.8714 11.3857C19.8714 16.2379 15.9379 20.1714 11.0857 20.1714H3.17303C2.3968 20.1714 2.00806 19.2251 2.55694 18.6716L4.27635 16.9378C3.04094 15.4245 2.3 13.4916 2.3 11.3857C2.3 6.5335 6.2335 2.60001 11.0857 2.60001C15.9379 2.60001 19.8714 6.5335 19.8714 11.3857ZM11.9555 7.87143C11.9555 7.38621 11.5641 6.99286 11.0813 6.99286C10.5985 6.99286 10.2071 7.38621 10.2071 7.87143V11.3857C10.2071 11.8709 10.5985 12.2643 11.0813 12.2643C11.5641 12.2643 11.9555 11.8709 11.9555 11.3857V7.87143ZM11.0813 14.0214C10.5985 14.0214 10.2071 14.4148 10.2071 14.9C10.2071 15.3852 10.5985 15.7786 11.0813 15.7786H11.0901C11.5729 15.7786 11.9643 15.3852 11.9643 14.9C11.9643 14.4148 11.5729 14.0214 11.0901 14.0214H11.0813Z"
            fill="#39CB60"
          />
        </svg>
      </div>
      <div class="text">
        <span class="subtitle">{{ aproove.title || "Поторопитесь!" }}</span>
        <span>
          {{
            aproove.title ||
            "Заявки временно принимаются с высокой вероятностью одобрения"
          }}</span
        >
      </div>
    </div>
    <div class="status">
      <div class="status-top">
        <div class="icon">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="89"
            height="89"
            viewBox="0 0 89 89"
            fill="none"
          >
            <rect
              width="88.6723"
              height="88.6723"
              rx="22.3149"
              fill="#FABB18"
              fill-opacity="0.1"
            />
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M42.6628 35.9768C42.6745 35.8238 42.8021 35.7057 42.9555 35.7057H44.253C44.4039 35.7057 44.5302 35.82 44.5452 35.9701L45.4363 44.8812L51.7112 48.4669C51.8027 48.5191 51.8592 48.6164 51.8592 48.7218V50.0021C51.8592 50.1957 51.6751 50.3363 51.4883 50.2854L42.0002 47.6977C41.8643 47.6606 41.7739 47.5323 41.7847 47.3919L42.6628 35.9768Z"
              fill="#FABB18"
            />
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M33.9977 23.5948C33.8426 23.41 33.5431 23.4807 33.4872 23.7154L30.9341 34.419C30.8885 34.6102 31.04 34.7914 31.2363 34.7802L42.2471 34.1563C42.4884 34.1426 42.6108 33.8595 42.4555 33.6744L39.4703 30.1168C41.0733 29.5691 42.7732 29.283 44.5186 29.283C53.1334 29.283 60.117 36.2667 60.117 44.8814C60.117 53.4962 53.1334 60.4798 44.5186 60.4798C35.9039 60.4798 28.9202 53.4962 28.9202 44.8814C28.9202 43.4352 29.1161 42.0188 29.4979 40.6574L25.9641 39.6661C25.4988 41.3249 25.25 43.0741 25.25 44.8814C25.25 55.5232 33.8769 64.15 44.5186 64.15C55.1604 64.15 63.7872 55.5232 63.7872 44.8814C63.7872 34.2396 55.1604 25.6128 44.5186 25.6128C41.842 25.6128 39.2929 26.1585 36.9765 27.1448L33.9977 23.5948Z"
              fill="#FABB18"
            />
          </svg>
        </div>
        <div class="currentDate">
          По состоянию на
          {{ new Date().getDate().toString().padStart(2, "0") }}.{{
            (new Date().getMonth() + 1).toString().padStart(2, "0")
          }}.{{ new Date().getFullYear() }}
          <span
            >{{ new Date().getHours().toString().padStart(2, "0") }}:{{
              new Date().getMinutes().toString().padStart(2, "0")
            }}</span
          >
        </div>
      </div>
      <div class="status-bottom">
        {{ aproove.title || "Данная компания одобряет 70% заявок" }}
      </div>
    </div>
    <v-btn
      style="
        background: linear-gradient(276deg, #2ed573 44.33%, #7bed9f 98.56%);
        margin-bottom: 11px;
      "
      >{{ aproove.buttonText || "Получить" }}</v-btn
    >
    <div class="timer">Вы будете перенаправлены на оффер через: {{ time }}</div>
  </div>
</template>

<style lang="scss" scoped>
.content {
  padding: 23px 12px 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  flex-direction: column;
  gap: 10px;
  .title {
    color: #1c1c1c;
    font-size: 35.022px;
    font-style: normal;
    font-weight: 600;
    line-height: normal;
  }

  .divider {
    background: linear-gradient(270deg, #d1d1d1 0%, #fff 50%, #d1d1d1 100%);
    height: 2px;
    width: 61%;
  }

  .logo {
    display: flex;
    min-width: 312px;
    padding: 10px;
    flex-direction: column;
    align-items: flex-start;
    gap: 10px;
    height: 146px;
  }

  .snackbar {
    display: flex;
    align-items: flex-start;
    border-radius: 20px;
    background: #f8f8f8;
    overflow: hidden;
    .icon {
      background: #d6ffcc;
      display: flex;
      width: 42.171px;
      padding: 0px 10.543px;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      flex-shrink: 0;
      align-self: stretch;
    }
    .text {
      display: flex;
      padding: 14.057px;
      align-items: flex-start;
      gap: 14.057px;
      flex: 1 0 0;
      flex-direction: column;
      align-items: flex-start;
      gap: 3.514px;
      flex: 1 0 0;
      span {
        color: $neutral-Black;
        font-size: 14px;
        font-style: normal;
        font-weight: 500;
        line-height: 140%; /* 19.6px */
      }
      .subtitle {
        align-self: stretch;
        color: $neutral-Black;
        font-size: 12.3px;
        font-style: normal;
        font-weight: 600;
        line-height: 140%; /* 17.22px */
      }
    }
  }

  .status {
    padding: 18px 13px 27px;

    width: 100%;
    position: relative;
    margin-bottom: 11px;

    flex-shrink: 0;
    border-radius: 19.966px;
    background: rgba(248, 248, 248, 0.8);
    box-shadow: 0px 9.396px 18.204px 0px rgba(0, 0, 0, 0.01);
    display: flex;
    align-items: flex-start;
    flex-direction: column;
    gap: 13px;

    &::after {
      content: "";
      position: absolute;
      top: 0;
      right: -10%;
      width: 20%;
      height: 100%;
      background: rgba(248, 248, 248, 0.8);
    }
    .status-top {
      display: flex;
      gap: 7px;

      .currentDate {
        display: flex;
        flex-direction: column;
        gap: 15px;
        align-items: flex-start;
        color: #000;
        font-size: 16.443px;
        font-style: normal;
        font-weight: 400;
        line-height: normal;
        span {
          color: #000;
          font-size: 25.838px;
          font-style: normal;
          font-weight: 700;
          line-height: normal;
        }
      }
    }
    .status-bottom {
      color: #000;
      text-align: center;
      font-size: 16.443px;
      font-style: normal;
      font-weight: 600;
      line-height: normal;
      text-align: center;
    }
  }
  .v-btn {
    margin: 0 auto;
    min-width: 250px;
    min-height: 50px;
    border-radius: 30px;
    color: #000;
    text-align: center;
    font-family: "Mulish" !important;
    font-size: 18px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    text-transform: capitalize;
  }

  .timer {
    color: #000;
    text-align: center;
    font-family: "Mulish";
    font-size: 15px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
  }
}
</style>
