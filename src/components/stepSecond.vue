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
                   <form data-step="2" class="step default-form">
                      <div class="row">
                        <!-- Input -->
                        <div class="form-group col-lg-8 col-md-10 col-12 d-flex formGruopMedia">
                          <label class="d-none576 required_field">Регион</label>
                          <InputSelect :options="regions" :error="$v.value.region.$error" @change="(data) => $v.value.region.$model = data._id" isSearchable></InputSelect>
                        </div>
                        <div class="form-group col-lg-8 col-md-10 col-12 d-flex formGruopMedia">
                          <label class="d-none576">Адрес</label>
                          <input
                            type="text"
                            v-model="value.address"
                            placeholder="Шайхантахур, улица Зафарабад, 7-дом"
                          />
                        </div>
                        <div class="form-group col-lg-8 col-md-10 col-12 d-flex formGruopMedia">
                          <label class="d-none576">График работы</label>
                          <InputSelect :options="typeOfEmployments" @change="(data) => value.typeOfEmployment = data._id"></InputSelect>
                        </div>
                        <div class="form-group col-lg-8 col-md-10 col-12 d-flex formGruopMedia">
                          <label class="d-none576">Опыт работы</label>
                          <InputSelect :options="experiences" @change="(data) => value.experience = data._id"></InputSelect>
                        </div>
                        <div :class="{invalid: !$v.value.tgUsername.required && $v.value.tgUsername.$dirty}" style="margin-top: -10px; padding-top: 10px !important;" class="contact-zone col-lg-8 col-md-10 col-12 p-0">
                          <div class="form-group col-12 d-flex formGruopMedia"
                            style="margin-bottom: 23px"
                          >
                            <label class="d-block d-none576">Телефон номер</label>
                            <div class="phone_numbers width-100">
                              <div 
                                class="phone_number" 
                                v-for="(phoneNumber, index) of value.phoneNumber"
                                :key="index"
                                ref="phones">
                                <the-mask 
                                  v-model="value.phoneNumber[index]"
                                  mask="(##) ###-##-##"
                                  type="tel" 
                                  class="important"
                                  :class="{invalid: $v.value.phoneNumber.$each[index].$invalid}"
                                  :masked="true" 
                                  placeholder="(00) 123-45-67">
                                </the-mask>
                                <button class="delete_area_phone_number" @click.prevent="deletePhoneNumber(index)">
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
                                <p v-if="$v.value.phoneNumber.$each[index].$invalid" class="invalid_feedback">
                                  Некорректный формат. Пример: (99) 999-99-99
                                </p>
                              </div>
                              <a
                                href=""
                                @click.prevent="addPhoneNumber"
                                class="d-block"
                                id="addNewPhoneNumber"
                                style="margin-top: 10px"
                                >+ Добавить телефон номер
                              </a>
                            </div>
                          </div>
                          <div class="form-group col-12 d-flex formGruopMedia">
                            <label class="d-block d-none576">Телеграм</label>
                            <div class="phone_numbers width-100">
                              <the-mask 
                                mask="@FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF"
                                v-model="$v.value.tgUsername.$model" 
                                :masked="true" 
                                :tokens="hexTokens"
                                class="important"
                                :class="{invalid: !$v.value.tgUsername.minLength}"
                                placeholder="@username_telegram">
                              </the-mask>
                              <p v-if="!$v.value.tgUsername.minLength" class="invalid_feedback my-2">
                                Данное поле должно содержать минимум 6 символов
                              </p>
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
            <label for=""></label>
            <div class="btn-box mt-5">
              <a
                @click="prevStep"
                class="theme-btn btn-style-five btn_prev"
                style="
                  width: 145px;
                  height: 45px;
                  color: #343338;
                  font-size: 18px;
                "
                ><span class="btn-title">Назад</span></a
              >
              <a
                @click.once="nextStep"
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
      </div>
    </form>
  </div>
</template>

<script>
import { required, requiredIf, minLength } from 'vuelidate/lib/validators'
import { TheMask } from 'vue-the-mask'
import InputSelect from '@/components/Inputs/InputSelect'

export default {
  components: { TheMask, InputSelect },
  props: { value: Object, regions: Array, typeOfEmployments: Array, experiences: Array },
  data() {
    return {
      hexTokens: {
        F: {
          pattern: /[a-zA-Z0-9_]/
        }
      },
    }
  },
  validations: {
    value: {
      region: {
        required
      },
      phoneNumber: {
        $each: {
          minLength: minLength(14)
        },
      },
      tgUsername: {
        minLength: minLength(6),
        required: requiredIf(function() {
          for (let index = 0; index < this.value.phoneNumber.length; index++) {
            if(this.value.phoneNumber[index].length == 14) return false
            if(index == this.value.phoneNumber.length - 1) return true
          }
        }),
      }
    }
  },
  methods: {
    nextStep() {
      this.$v.value.$touch()
      if(!this.$v.value.$invalid) this.$emit("next-step")
    },
    prevStep() {
      this.$emit("prev-step")
    },
    async addPhoneNumber() {
      await this.value.phoneNumber.push("")
      this.$refs.phones[this.$refs.phones.length - 1].firstChild.focus()
    },
    deletePhoneNumber(index) {
      if(this.value.phoneNumber.length > 1) this.value.phoneNumber.splice(index, 1)
    }
  },
};
</script>

<style scoped>
.contact-zone{
  position: relative;
  border-width: 2px !important;
  border-style: dashed !important;
  border-radius: 10px;
  border-color: transparent;
  transition: border-color ease 500ms;
}
.contact-zone::before{
  opacity: 0; 
  transition: all ease 300ms;
  content: "Наберите хоть одну контакт";
  position: absolute;
  border-color: rgb(243, 111, 124);
  color: rgb(243, 111, 124);
  left: 10px;
  font-weight: 700;
  bottom: 0px;
}
.invalid.contact-zone::before{
  content: "Покажите хоть одну контакт";
  position: absolute;
  opacity: 1;
  border-color: rgb(243, 111, 124);
  color: rgb(243, 111, 124);
  left: 10px;
  font-weight: 700;
  bottom: 0px;
}

</style>
