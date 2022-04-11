<template>
  <div class="page-wrapper">
    <!-- Dashboard -->
    <section class="user-dashboard">
      <div class="auto-container">
        <div class="dashboard-outer">
          <div class="row">
            <div class="col-12 p-0">
              <!-- Ls widget -->
              <div class="ls-widget">
                <div class="tabs-box">
                  <div id="vacancy_form" class="widget-content">
                    <form data-step="1" class="step default-form">
                      <div class="row">
                        <!-- Input -->
                        <div
                          class="
                            form-group
                            col-lg-8 col-md-10 col-12
                            d-flex
                            formGruopMedia
                          "
                        >
                          <label class="d-none576 required_field">Должность</label>
                          <input
                            v-model="$v.value.position.$model"
                            type="text"
                            :class="{ invalid: $v.value.position.$error }"
                            placeholder="Оператор в колл центр"
                          />
                        </div>
                        <div
                          class="
                            form-group
                            col-lg-8 col-md-10 col-12
                            d-flex
                            formGruopMedia
                          "
                        >
                          <label class="d-none576">Компания</label>
                          <input
                            v-model="value.company"
                            type="text"
                            data-input="company"
                            placeholder="Faktura.uz или OOO SPACE ONLINE GENESIS"
                          />
                        </div>
                        <div
                          class="
                            form-group
                            col-lg-8 col-md-10 col-12
                            d-flex
                            formGruopMedia
                          "
                        >
                          <label @click="$emit('showSelectCategory')" class="d-none576 required_field">Специализация</label>
                          <div @click="$emit('showSelectCategory')" :class="{invalid: $v.value.category.$error}" class="selector_category d-flex justify-content-between">
                            <span v-if="value.category.positionId">{{getPositionNameById}}</span>
                            <span v-else>Выбрать</span>
                            <span class="d-flex align-items-center text-secondary">
                              <svg xmlns="http://www.w3.org/2000/svg" width="21" height="21" fill="currentColor" class="bi bi-box-arrow-in-up-right" viewBox="0 0 16 16">
                                <path fill-rule="evenodd" d="M6.364 13.5a.5.5 0 0 0 .5.5H13.5a1.5 1.5 0 0 0 1.5-1.5v-10A1.5 1.5 0 0 0 13.5 1h-10A1.5 1.5 0 0 0 2 2.5v6.636a.5.5 0 1 0 1 0V2.5a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 .5.5v10a.5.5 0 0 1-.5.5H6.864a.5.5 0 0 0-.5.5z"/>
                                <path fill-rule="evenodd" d="M11 5.5a.5.5 0 0 0-.5-.5h-5a.5.5 0 0 0 0 1h3.793l-8.147 8.146a.5.5 0 0 0 .708.708L10 6.707V10.5a.5.5 0 0 0 1 0v-5z"/>
                              </svg>
                            </span>
                          </div>
                        </div>
                        <div
                          class="
                            form-group
                            col-lg-8 col-md-10 col-12
                            d-flex
                            formGruopMedia
                          "
                        >
                          <label class="d-block d-none576">Описание</label>
                          <div class="descriptions width-100">
                            <div class="square">
                              <div
                                class="description"
                                v-for="(item, index) of value.descriptions"
                                :key="index"
                              >
                                <div class="title d-flex">
                                  <span
                                    class="
                                      d-flex
                                      justify-content-center
                                      align-items-center
                                      mx-2
                                    "
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
                                  <button
                                    @click.prevent="deleteDescription(index)"
                                  >
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
                                  @input.prevent="onInputHandlerDescription(item)"
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
                          <label class="d-block required_field">Зарплата</label>
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

                            <div
                              v-if="!value.salary.contract"
                              class="d-flex formGruopMedia"
                              style="margin-top: 27px"
                            >
                              <InputSelect
                                :options="typeSalaries"
                                :default="value.salary.type"
                                @change="
                                  (data) => (value.salary.type = data._id)
                                "
                              ></InputSelect>
                              <label style="min-width: auto; margin-left: 14px"
                                >от</label
                              >
                              <input
                                class="formSalaryMedia"
                                :class="{
                                  invalid: $v.value.salary.from.$error,
                                }"
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
                              <InputSelect
                                :options="currencies"
                                :default="value.salary.currency"
                                @change="
                                  (data) => (value.salary.currency = data._id)
                                "
                              ></InputSelect>
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
        <div class="col-12">
          <div class="form-group d-flex">
            <label class="d-block"></label>
            <div class="btn-box mt-5">
              <a
                @click="nextStep"
                :disabled="$v.value.$invalid"
                class="theme-btn btn-style-two btn_next"
                style="
                  width: 175px;
                  height: 47px;
                  color: #343338;
                  font-size: 18px;
                "
                :style="{ opacity: $v.value.$invalid ? 0.5 : 1 }"
                ><span class="btn-title">Продолжить</span></a
              >
            </div>
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
import { required, requiredIf } from "vuelidate/lib/validators";
import InputSelect from "@/components/Inputs/InputSelect.vue";
export default {
  name: "stepFirst",
  components: {
    InputSelect: InputSelect,
  },
  props: { value: Object, categories: Array, currencies: Array, typeSalaries: Array },
  validations: {
    value: {
      position: { required },
      category: { 
        positionId: { required }
      },
      salary: {
        from: {
          contractOrFromSalary: requiredIf((salary = this) => {
            return !salary.contract;
          }),
        },
      },
    },
  },
  methods: {
    async addNewDescription() {
      await this.value.descriptions.push({ title: "", description: "" });
      this.$refs.descriptionTitle[
        this.$refs.descriptionTitle.length - 1
      ].focus();
    },
    deleteDescription(index) {
      if (this.value.descriptions.length > 1) this.value.descriptions.splice(index, 1);
    },
    onInputHandlerDescription(data) {
      let text = data.description.split("\n")
      text = text.map(piece => {
        let letter = piece.trim().split("")
        if(letter[0] !== "-" && letter.length){
          letter = ['- ', ...letter] 
          return letter.join("")
        }
        return letter.join("")
      })
      data.description = text.join('\n')
    },
    nextStep() {
      this.$v.value.$touch();
      if (!this.$v.value.$invalid) {
        this.$emit("next-step");
      }
    },
  },
  computed: {
    getPositionNameById() {
      if(this.categories.length){
        let searchProfession = this.categories.find(item => {
          return item._id === this.value.category.professionId
        })
  
        let searchPositionByProfession = searchProfession.positions.find(item => {
          return item._id === this.value.category.positionId
        })
        console.log(searchPositionByProfession.ruName);
        return searchPositionByProfession.ruName
      }
      return ""
    }
  },
  watch: {
    "$v.value.salary.from.$model"(text) {
      this.$v.value.salary.from.$model = text
        .replace(/[^\d]/g, "")
        .replace(/\d{1,3}(?=(\d{3})+(?!\d))/g, "$& ");
    },
    "value.salary.to"(text) {
      this.value.salary.to = text
        .replace(/[^\d]/g, "")
        .replace(/\d{1,3}(?=(\d{3})+(?!\d))/g, "$& ");
    },
  },
};
</script>

<style scoped>
  .selector_category {
    position: relative;
    cursor: pointer;
    width: 100%;
    display: block;
    height: 60px;
    line-height: 30px;
    padding: 15px 20px;
    font-size: 15px;
    color: #696969;
    background: #f0f5f7;
    border: 1px solid #f0f5f7;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    border-radius: 8px;
    -webkit-transition: all 300ms ease;
    -o-transition: all 300ms ease;
    transition: all 300ms ease;
  }
  .selector_category.invalid span{
    color: rgb(243, 111, 124) !important;
  }
</style>

