<template>
  <div class="page-wrapper">
    <!-- Preloader -->
    <div class="preloader"></div>
    <!-- End Preloader -->

    <!-- Main Header-->
    <Header></Header>
    <!--End Main Header -->

    <!--Page Title-->
    <section class="page-title">
      <div class="auto-container">
        <div class="title-outer">
          <h1>Создать вакансию</h1>
        </div>
      </div>
    </section>
    <!--End Page Title-->

    <section class="step_by_step d-flex align-items-center">
      <div class="auto-container">
        <div class="row align-items-center">
          <div class="col-12">
            <div class="d-flex align-items-center centerStepsBox">
              <div
                class="step"
                :class="{ active: step === 1 }"
                @click="step = 1"
              >
                <span class="step_number">1</span>
                <span class="step_text">Главное</span>
              </div>
              <span class="line"></span>
              <div
                class="step"
                :class="{ active: step === 2, disabled: step < 2 }"
                @click="() => {if (step > 2) step = 2}"
              >
                <span class="step_number">2</span>
                <span class="step_text">Детали</span>
              </div>
              <span class="line"></span>
              <div
                class="step"
                :class="{ active: step === 3, disabled: step < 3 }"
                @click="() => {if (step > 3) step = 3}"
              >
                <span class="step_number">3</span>
                <span class="step_text">Предпросмотр</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Dashboard -->
    <section class="user-dashboard">
      <div class="auto-container">
        <div class="dashboard-outer">
          <div class="row">
            <div class="col-12">
              <!-- Ls widget -->
              <div class="ls-widget">
                <div class="tabs-box">
                  <div id="vacancy_form" class="widget-content">
                    <stepFirst v-model="form" v-if="step === 1" @next-step="nextStep"></stepFirst>
                    <stepSecond v-model="form" v-if="step === 2" @prev-step="prevStep" @next-step="nextStep"></stepSecond>
                    <stepThird v-model="form" v-if="step === 3" @prev-step="prevStep" @next-step="nextStep"></stepThird>
                  </div>
                </div>
              </div>
            </div>
            <div class="col-12 col-lg-10">
              <!-- Ls widget -->
              <div class="ls-widget">
                <div class="tabs-box">
                  <div class="widget-content">
                    <form class="default-form"></form>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- End Dashboard -->

    <!-- Main Footer -->
    <Footer></Footer>
    <!-- End Main Footer -->
  </div>
</template>

<script>
import Header from "../components/headerMain.vue";
import Footer from "../components/footerMain.vue";
import stepFirst from "../components/stepFirst.vue";
import stepSecond from "../components/stepSecond.vue";
import stepThird from "../components/stepThird.vue";

export default {
  components: { Header, stepFirst, stepSecond, stepThird, Footer },
  name: "createVacancy",

  data() {
    return {
      step: 2,
      form: {
        position: "",
        company: "",
        category: {},
        descriptions: [
          { title: "Обязанности:", description: "" },
          { title: "Требования:", description: "" },
          { title: "Условия:", description: "" }
        ],
        salary: {
          contract: false,
          type: 0,
          from: "",
          to: "",
          currency: 0
        },
        region: null,
        address: "",
        typeOfEmployment: null,
        experience: null,
        phoneNumber: [""],
        tgUsername: "",
        lang: "ru"
      }
    };
  },

  methods: {
    prevStep() {
      if(this.step > 1) this.step--
      window.scrollTo(0, 0)
    },
    nextStep() {
      if(this.step < 3) this.step++
      window.scrollTo(0, 0)
    },
  },
};
</script>

<style>
  .invalid {
    border: 1px solid rgb(243, 111, 124) !important;
    background: #ffffff !important;
  }
  .invalid_feedback {
    font-size: 13px;
    margin-top: -10px;
    display: block;
    margin-left: 7px;
    margin-bottom: 0;
    color: rgb(243, 111, 124);
    font-weight: 700;
  }
  .invalid::placeholder {
    color:  rgba(220, 53, 69, 0.5) !important;
  }
</style>