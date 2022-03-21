<template>
  <div class="page-wrapper">

    <!-- Dashboard -->
    <section class="user-dashboard">
      <div class="auto-container">
        <div class="dashboard-outer">
          <div class="row">
            <div class="col-12 pNone">
              <!-- Ls widget -->
              <div class="ls-widget">
                <div class="tabs-box">
                  <div id="vacancy_form" class="widget-content">
                    <form data-step="1" class="step default-form">
                      <div class="row">
                        <!-- Input -->
                        <div class="form-group col-lg-8 col-md-10 col-12 d-flex formGruopMedia">
                          <label class="d-none576">Должность</label>
                          <input
                            v-model="$v.value.position.$model"
                            type="text"
                            :class="{invalid: $v.value.position.$error}"
                            placeholder="Оператор"
                          />
                        </div>
                        <div class="form-group col-lg-8 col-md-10 col-12 d-flex formGruopMedia">
                          <label class="d-none576">Компания</label>
                          <input
                            v-model="value.company"
                            type="text"
                            data-input="company"
                            placeholder="Faktura.uz или OOO SPACE ONLINE GENESIS"
                          />
                        </div>
                        <div class="form-group col-lg-8 col-md-10 col-12 d-flex formGruopMedia">
                          <label class="d-none576">Специализация</label>
                          <select class="chosen-select" v-model="$v.value.category.$model" :class="{invalid: $v.value.category.$error}">
                            <option v-for="(category, index) of categories" :key="index">{{category.ruName}}</option>
                          </select>
                        </div>
                        <div class="form-group col-lg-8 col-md-10 col-12 d-flex formGruopMedia">
                          <label class="d-block d-none576">Описание</label>
                          <div class="descriptions width-100">
                            <div class="square">
                              <div class="description" v-for="(item, index) of value.descriptions" :key="index">
                                <div class="title d-flex">
                                  <span
                                    class="d-flex justify-content-center align-items-center mx-2"
                                    ><svg
                                      xmlns="http://www.w3.org/2000/svg"
                                      width="17"
                                      height="17"
                                      viewBox="0 0 24 24"
                                      fill="none"
                                      stroke="#969696"
                                      stroke-width="3"
                                      stroke-linecap="round"
                                      stroke-linejoin="round"
                                      class="feather feather-edit-3"
                                    >
                                      <polygon
                                        points="14 2 18 6 7 17 3 17 3 13 14 2"
                                      />
                                      <line
                                        x1="3"
                                        y1="22"
                                        x2="21"
                                        y2="22"
                                      /></svg
                                  ></span>
                                  <input
                                    ref="descriptionTitle"
                                    type="text"
                                    v-model="item.title"

                                    placeholder="Название пункта..."
                                  />
                                  <button @click.prevent="deleteDescription(index)">
                                    <svg
                                      xmlns="http://www.w3.org/2000/svg"
                                      width="20"
                                      height="20"
                                      viewBox="0 0 24 24"
                                      fill="none"
                                      stroke="#B3B3B3"
                                      stroke-width="3"
                                      stroke-linecap="round"
                                      stroke-linejoin="round"
                                      class="feather feather-x"
                                    >
                                      <line x1="18" y1="6" x2="6" y2="18" />
                                      <line x1="6" y1="6" x2="18" y2="18" />
                                    </svg>
                                  </button>
                                </div>
                                <textarea
                                  class="mb-4"
                                  v-model="item.description"
                                  placeholder="Информация о вакансия..."
                                ></textarea>
                              </div>
                            </div>
                            <a
                              class="d-block"
                              href=""
                              @click.prevent="addNewDescription"
                              style="margin-top: -0.5rem"
                              >+ Добавить пункт
                            </a>
                          </div>
                        </div>
                      </div>
                      <div class="row">
                        <div class="form-group col-10 d-flex formGruopMedia">
                          <label class="d-block">Зарплата</label>
                          <div class="salary">
                            <div class="radio-box">
                              <input
                                type="radio"
                                @click="$v.value.$model.salary.contract = true"
                                :checked="value.salary.contract"
                                id="contract"
                              />
                              <label for="contract">Договорная</label>
                            </div>
                            <div class="radio-box mt-4">
                              <input
                                type="radio"
                                @click="$v.value.$model.salary.contract = false"
                                id="salary"
                                :checked="!value.salary.contract"
                              />
                              <label for="salary">Указать</label>
                            </div>

                            <div v-if="!value.salary.contract" class="d-flex formGruopMedia" style="margin-top: 27px">
                              <select class="chosen-select">
                                <option v-for="(typeSalary, index) of typeSalaries" :key="index" :value="typeSalary._id">{{typeSalary.ruName}}</option>
                              </select>
                              <label style="min-width: auto; margin-left: 14px"
                                >от</label
                              >
                              <input
                                class="formSalaryMedia"
                                :class="{invalid: $v.value.salary.from.$error}"
                                style="margin: 0 14px"
                                v-model="$v.value.salary.from.$model"
                                type="tel"
                                placeholder="2 000 000"
                              />
                              <label style="min-width: auto">до</label>
                              <input
                                class="formSalaryMedia mb-2--767"
                                style="margin: 0 20px 0 14px"
                                v-model="value.salary.to"
                                type="tel"
                                placeholder="3 000 000"
                              />
                              <select class="chosen-select">
                                <option v-for="(currency, index) of currencies" :key="index" :value="currency._id">{{currency.ruName}}</option>
                              </select>
                            </div>
                          </div>
                        </div>
                      </div>
                    </form>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <form class="default-form navigation_form">
      <div class="row">
        <div class="form-group d-flex">
          <label for=""></label>
          <div class="btn-box mt-5 ml-4">
            <a
              @click="nextStep"
              :disabled="$v.value.$invalid"
              class="theme-btn btn-style-two btn_next"
              style="
                width: 175px;
                height: 45px;
                color: #343338;
                font-size: 18px;
                margin-left: 7px;
              "
              :style="{opacity: $v.value.$invalid ? 0.5 : 1}"
              ><span class="btn-title">Продолжить</span></a
            >
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
import { required, requiredIf } from 'vuelidate/lib/validators'
import { APIHOST } from "@/settings"
export default {
  name: "stepFirst",
  props: {value: Object},
  validations: {
    value: {
      position: { required },
      category: { required },
      salary: {
          from: {
            contractOrFromSalary: requiredIf((salary = this) => {
              return !salary.contract
            })
          }
      },
    }
  },
  data() {
    return {
      categories: [],
      currencies: [],
      typeSalaries: []
    }
  },
  methods: {
    load() {
      this.getCategories()
      this.getCategories()
      this.getCurrencies()
      this.getTypeSalaries()
    },
    async getCategories() {
      let categories = await fetch(`${APIHOST}/api/vacancy/get-categories`).then(data => {
          if(data.status >= 500) return { success: false, error: "Ошибка при получения данных о категрии с сервера", data: {} }
          return data.json()
        })
      if(categories.success) {
        this.categories = categories.data
      }else{ 
        alert(categories.error)
      }
    },
    async getCurrencies() {
      let currencies = await fetch(`${APIHOST}/api/vacancy/get-currencies`).then(data => {
          if(data.status >= 500) return { success: false, error: "Ошибка при получения данных о категрии с сервера", data: {} }
          return data.json()
        })
      if(currencies.success) {
        this.currencies = currencies.data
      }else{ 
        alert(currencies.error)
      }
    },
    async getTypeSalaries() {
      let typeSalaries = await fetch(`${APIHOST}/api/vacancy/get-type-salaries`).then(data => {
          if(data.status >= 500) return { success: false, error: "Ошибка при получения данных о категрии с сервера", data: {} }
          return data.json()
        })
      if(typeSalaries.success) {
        this.typeSalaries = typeSalaries.data
      }else{ 
        alert(typeSalaries.error)
      }
    },
    async addNewDescription() {
      await this.value.descriptions.push({title: "", description: ""})
      this.$refs.descriptionTitle[this.$refs.descriptionTitle.length - 1].focus()
    },
    deleteDescription(index) {
      if(this.value.descriptions.length > 1) this.value.descriptions.splice(index, 1)
    },
    nextStep() {
      this.$v.value.$touch()
      if(!this.$v.value.$invalid){
        this.$emit("next-step")
      }
    },
  },
  watch: {
    '$v.value.salary.from.$model'(text) {
      this.$v.value.salary.from.$model = text.replace(/[^\d]/g, '').replace(/\d{1,3}(?=(\d{3})+(?!\d))/g, '$& ');
    },
    'value.salary.to'(text) {
      this.value.salary.to = text.replace(/[^\d]/g, '').replace(/\d{1,3}(?=(\d{3})+(?!\d))/g, '$& ');
    }
  },
  created() {
    this.load()
  }
};
</script>

