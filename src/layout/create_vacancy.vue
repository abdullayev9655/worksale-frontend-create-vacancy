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
        <div v-if="step < 4" class="title-outer">
          <template v-if="step === 3">
            <h2 class="text-left mb-2" style="color: #fec900">{{form.position}}</h2>
            <h3 class="text-left text-white">{{salary}}</h3>
          </template>
          <template v-else>
            <h1>Создать вакансию</h1>
          </template>
        </div>
      </div>
    </section>
    <!--End Page Title-->

    <section v-if="step < 4" class="step_by_step d-flex align-items-center">
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
                    <stepFirst v-model="form" v-if="step === 1" @next-step="nextStep" @showSelectCategory="showSelectCategory = true" :categories="categories" :currencies="currencies" :typeSalaries="typeSalaries" ></stepFirst>
                    <stepSecond v-model="form" v-if="step === 2" @prev-step="prevStep" @next-step="nextStep" :regions="regions" :typeOfEmployments="typeOfEmployments" :experiences="experiences"></stepSecond>
                    <stepThird :vacancy="form"  v-if="step === 3" @prev-step="prevStep" @create-vacancy="createVacancy" :options="{salary, categories, currencies, typeSalaries, regions, typeOfEmployments, experiences}"></stepThird>
                    <moderation v-if="step === 4"></moderation>
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
    
    <transition name="loading_fade">
      <SelectPositionByProfession v-if="categories.length && showSelectCategory" v-model="form" @hidden="showSelectCategory = false" :categories="categories"></SelectPositionByProfession>
      <Loader v-if="loading" />
    </transition>
  </div>
</template>

<script>
import { APIHOST } from "@/settings";
import Header from "../components/headerMain.vue";
import Footer from "../components/footerMain.vue";
import stepFirst from "../components/stepFirst.vue";
import stepSecond from "../components/stepSecond.vue";
import stepThird from "../components/stepThird.vue";
import moderation from '@/components/moderation';
import Loader from '@/components/Generic/Loader';
import SelectPositionByProfession from '@/components/Select/SelectPositionByProfession'

export default {
  components: { Header, stepFirst, stepSecond, stepThird, moderation, Footer, Loader, SelectPositionByProfession },
  name: "createVacancy",

  data() {
    return {
      step: 1,
      loading: false,
      showSelectCategory: false,
      form: {
        imageBase64: "",
        position: "СПЕЦИАЛИСТ ПО ЛОГИСТИКЕ",
        company: "OOO Alem Agro Holding",
        category: {professionId: null, positionId: null},
        descriptions: [
          { title: "Обязанности:", description: "- Материальная ответственность за товар на складе;\n- Координация отгрузки и отслеживание грузов;\n- Анализ остатков на складах;\n- Инвентаризация на складе." },
          { title: "Требования:", description: "- Уверенный пользователь ПК;\n- Знание русского будет плюсом." },
          { title: "Условия:", description: "- Официальное оформление;\n- Стабильная оплата;\n- Корпоративное обучение при трудоустройстве;\n- Полный рабочий день с 9.00 до 18.00 (выход на пол-дня по субботам в «сезон»);" }
        ],
        salary: {
          contract: false,
          type: 0,
          from: "200",
          to: "500",
          currency: 1
        },
        region: 5,
        address: "ул. Шота Руставели 121, рядом Братские могилы",
        typeOfEmployment: 0,
        experience: 0,
        phoneNumber: ["(97) 714-11-71"],
        tgUsername: "@thisisayau",
        lang: "ru"
      },
      // form: {
      //   position: "",
      //   company: "",
      //   category: {professionId: null, positionId: null},
      //   descriptions: [
      //     { title: "Обязанности:", description: "" },
      //     { title: "Требования:", description: "" },
      //     { title: "Условия:", description: "" }
      //   ],
      //   salary: {
      //     contract: false,
      //     type: 0,
      //     from: "",
      //     to: "",
      //     currency: 0
      //   },
      //   region: null,
      //   address: "",
      //   typeOfEmployment: null,
      //   experience: null,
      //   phoneNumber: [""],
      //   tgUsername: "",
      //   lang: "ru"
      // },
      regions: [],
      categories: [],
      currencies: [],
      experiences: [],
      typeSalaries: [],
      typeOfEmployments: [],
      previewBase64: ""
    };
  },
  computed: {
    salary(){
      if(this.form.salary.contract){
        return "Договорная"
      }
      else{
        if(this.form.salary.currency){
          return this.form.salary.to ? "от "+this.form.salary.from+"$ до "+this.form.salary.to+"$" : "от "+this.form.salary.from+"$"
        }
        else{
          return this.form.salary.to ? "от "+this.form.salary.from+" до "+this.form.salary.to+" сум" : "от "+this.form.salary.from+" сум"
        }
      }
    }
  },
  methods: {
    prevStep() {
      if(this.step > 1) this.step--
      window.scrollTo(0, 0)
    },
    async nextStep() {
      if(this.step < 4) {
        if(this.step === 2) await this.getPreview()
        this.step++
      }
      window.scrollTo(0, 0)
    },
    load() {
      this.getCategories()
      this.getCurrencies()
      this.getTypeSalaries()
      this.getRegions()
      this.getExperiences()
      this.getTypeOfEmployments()
    },
    async getCategories() {
      let categories = await fetch(
        `${APIHOST}/api/vacancy/get-categories`
      ).then((data) => {
        if (data.status >= 500)
          return {
            success: false,
            error: "Ошибка при получения данных о категрии с сервера",
            data: {},
          };
        return data.json();
      });
      if (categories.success) {
        this.categories = categories.data;
      } else {
        alert(categories.error);
      }
    },
    async getCurrencies() {
      let currencies = await fetch(
        `${APIHOST}/api/vacancy/get-currencies`
      ).then((data) => {
        if (data.status >= 500)
          return {
            success: false,
            error: "Ошибка при получения данных о категрии с сервера",
            data: {},
          };
        return data.json();
      });
      if (currencies.success) {
        this.currencies = currencies.data;
      } else {
        alert(currencies.error);
      }
    },
    async getTypeSalaries() {
      let typeSalaries = await fetch(
        `${APIHOST}/api/vacancy/get-type-salaries`
      ).then((data) => {
        if (data.status >= 500)
          return {
            success: false,
            error: "Ошибка при получения данных о категрии с сервера",
            data: {},
          };
        return data.json();
      });
      if (typeSalaries.success) {
        this.typeSalaries = typeSalaries.data;
      } else {
        alert(typeSalaries.error);
      }
    },
    async getRegions() {
      let regions = await fetch(`${APIHOST}/api/vacancy/get-regions`).then(data => {
          if(data.status >= 500) return { success: false, error: "Ошибка при получения данных о категрии с сервера", data: {} }
          return data.json()
        })
      if(regions.success) {
        this.regions = regions.data
      }else{ 
        alert(regions.error)
      }
    },
    async getExperiences() {
      let experiences = await fetch(`${APIHOST}/api/vacancy/get-experiences`).then(data => {
          if(data.status >= 500) return { success: false, error: "Ошибка при получения данных о категрии с сервера", data: {} }
          return data.json()
        })
      if(experiences.success) {
        this.experiences = experiences.data
      }else{ 
        alert(experiences.error)
      }
    },
    async getTypeOfEmployments() {
      let typeOfEmployments = await fetch(`${APIHOST}/api/vacancy/get-type-of-employments`).then(data => {
          if(data.status >= 500) return { success: false, error: "Ошибка при получения данных о категрии с сервера", data: {} }
          return data.json()
        })
      if(typeOfEmployments.success) {
        this.typeOfEmployments = typeOfEmployments.data
      }else{ 
        alert(typeOfEmployments.error)
      }
    },
    async getPreview() {
      this.loading = true
      let previewBase64 = await fetch(`${APIHOST}/api/vacancy/get-preview`, {
        method: "POST",
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({
          position: this.form.position,
          company: this.form.company,
          salary: this.form.salary,
          typeOfEmployment: this.form.typeOfEmployment,
          experience: this.form.experience,
          region: this.form.region,
          lang: 'uz',
        })
      })
      .then(data => {
        if(data.status >= 500) return { success: false, error: "Ошибка при получения изображение с сервера", data: {} }
        return data.json()
      })
      if(previewBase64.success) {
        this.form.imageBase64 = previewBase64.data
      }else{ 
        alert(previewBase64.error)
      }
      this.loading = false
    },
    async createVacancy() {
      this.loading = true
      let vacancy = await fetch(`${APIHOST}/api/vacancy/create`, {
        method: "POST",
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({
          position: this.form.position,
          company: this.form.company,
          category: this.form.category,
          descriptions: this.form.descriptions,
          salary: this.form.salary,
          region: this.form.region,
          address: this.form.address,
          typeOfEmployment: this.form.typeOfEmployment,
          experience: this.form.experience,
          phoneNumber: this.form.phoneNumber,
          tgUsername: this.form.tgUsername,
          lang: this.form.lang
        })
      })
      .then(data => {
        if(data.status >= 500) return { success: false, error: "Ошибка сервера, попробуйте еще раз или обратитесь нам", data: {} }
        return data.json()
      })
      if(vacancy.success) {
        this.nextStep()
      }else{ 
        alert(vacancy.error)
      }
      this.loading = false
    }
  },
  created() {
    this.load()
  }
};
</script>

<style>
  .invalid {
    border: 1px solid rgb(243, 111, 124) !important;
    background: #ffffff !important;
  }
  .required_field::after {
    content: "*";
    font-family: serif;
    font-size: 18px;
    color: red;
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
  
  .loading_fade-enter-active, .loading_fade-leave-active {
    transition: opacity .25s;
  }
  .loading_fade-enter, .loading_fade-leave-to /* .fade-leave-active до версии 2.1.8 */ {
    opacity: 0;
  }
</style>