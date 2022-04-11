<template>
  <div class="page-wrapper">
    <!-- Dashboard -->
    <section class="user-dashboard">
      <div class="auto-container p-0">
        <div class="dashboard-outer">
          <div class="row">
            <div class="col-12 p-0">
              <!-- Ls widget -->
              <div class="ls-widget">
                <div class="tabs-box">
                  <div id="vacancy_form" class="widget-content">
                    <form data-step="3" class="step default-form">
                      <section class="job-detail-section">
                        <div class="job-detail-outer">
                          <div class="auto-container">
                            <div class="row">
                              <div class="col-12 col-md-6">
                                <div class="content-column">
                                  <div class="job-block-outer">
                                    <!-- Job Block -->
                                    <div class="job-block-seven style-two">
                                      <div class="inner-box">
                                        <div class="content">
                                          <h4 class="text-primary">
                                            {{ vacancy.company }}
                                          </h4>
                                          <h5 class="text-muted">
                                            {{ data.region.ruName }}
                                          </h5>
                                          <div
                                            class="btn-box mt-4"
                                            v-if="!showPhone"
                                          >
                                            <a
                                              id="showContact"
                                              @click="showPhone = true"
                                              class="theme-btn btn-style-two"
                                              ><span class="btn-title"
                                                >Показать контакты</span
                                              ></a
                                            >
                                          </div>
                                        </div>
                                      </div>
                                    </div>
                                  </div>
                                  <div class="job-detail">
                                    <transition name="visible-phone">
                                      <div class="mb-4 phone" v-if="showPhone">
                                        <h4>Контактная информация</h4>
                                        - Телефон номер:
                                        {{ vacancy.phoneNumber.join(", ")
                                        }}<br />
                                        - Тепеграм: {{ vacancy.tgUsername
                                        }}<br />
                                      </div>
                                    </transition>
                                    <div
                                      v-for="(
                                        item, index
                                      ) of vacancy.descriptions"
                                      :key="index"
                                    >
                                      <h4>{{ item.title }}</h4>
                                      <pre>{{ item.description }}</pre>
                                    </div>
                                  </div>
                                </div>

                                <div class="form-group d-flex mt-5">
                                  <div class="btn-box mediaBtnBoxSm mt-5">
                                    <a
                                      @click="prevStep"
                                      class="theme-btn btn-style-five btn_prev"
                                      style="
                                        height: 49px !important;
                                        color: #343338;
                                        font-size: 18px;
                                      "
                                      ><span class="btn-title">Назад</span></a
                                    >
                                    <a
                                      @click.once="nextStep"
                                      class="theme-btn btn-style-two btn_next"
                                      style="
                                        height: 49px !important;
                                        color: #343338;
                                        font-size: 18px;
                                        margin-left: 7px;
                                      "
                                      ><span class="btn-title"
                                        >Опубликовать</span
                                      ></a
                                    >
                                  </div>
                                </div>
                              </div>
                              <div class="col-auto">
                                <instagram
                                  :details="{
                                    ...vacancy,
                                    data: {
                                      ...data,
                                      salary: this.options.salary,
                                    },
                                  }"
                                ></instagram>
                              </div>
                            </div>
                          </div>
                        </div>
                      </section>
                    </form>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import instagram from "@/components/instagram";

export default {
  components: { instagram },
  props: {
    vacancy: {
      type: Object,
      required: true,
    },
    options: {
      type: Object,
    },
  },
  data() {
    return {
      showPhone: false,
    };
  },
  methods: {
    nextStep() {
      this.$emit("create-vacancy");
    },
    prevStep() {
      this.$emit("prev-step");
    },
  },
  computed: {
    data() {
      return {
        category: this.options.categories.find(
          (item) => item._id === this.vacancy.category
        ),
        currency: this.options.currencies.find(
          (item) => item._id === this.vacancy.salary.currency
        ),
        type: this.options.typeSalaries.find(
          (item) => item._id === this.vacancy.salary.type
        ),
        region: this.options.regions.find(
          (item) => item._id === this.vacancy.region
        ),
        typeOfEmployment: this.options.typeOfEmployments.find(
          (item) => item._id === this.vacancy.typeOfEmployment
        ),
        experience: this.options.experiences.find(
          (item) => item._id === this.vacancy.experience
        ),
      };
    },
  },
};
</script>

<style scoped>
.visible-phone-enter-active,
.visible-phone-leave-active {
  -webkit-transition: all 0.35s ease-in;
  -moz-transition: all 0.35s ease-in;
  -o-transition: all 0.35s ease-in;
  -ms-transition: all 0.35s ease-in;
  transition: all 0.35s ease-in;
}
.visible-phone-enter,
.visible-phone-leave-to {
  opacity: 0;
  margin-left: -7px;
}

.job-detail h4 {
  margin-bottom: 16px;
}

.job-detail pre {
  margin-bottom: 20px;
  font-size: inherit;
  font-family: "Roboto", sans-serif;
  white-space: pre-wrap;
  white-space: -moz-pre-wrap;
  white-space: -pre-wrap;
  white-space: -o-pre-wrap;
  word-wrap: break-word;
}

.btn-box .btn_next {
  transition: width 0.5s ease;
}
</style>