<template>
  <div class="page-wrapper">

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
                     <form data-step="3" class="step default-form">
                      <section class="job-detail-section">
                        <div class="job-detail-outer">
                          <div class="auto-container">
                            <div class="row">
                              <div
                                class="content-column col-lg-8 col-md-12 col-sm-12"
                              >
                                <div class="job-block-outer">
                                  <!-- Job Block -->
                                  <div class="job-block-seven style-two">
                                    <div class="inner-box">
                                      <div class="content">
                                        <h4>КОНТЕНТ-МЕНЕДЖЕР 1</h4>
                                        <ul class="job-info">
                                          <li>
                                            <span
                                              class="icon flaticon-briefcase"
                                            ></span>
                                            Dasturchi
                                          </li>
                                          <li>
                                            <span
                                              class="icon flaticon-clock-3"
                                            ></span>
                                            08.12.2021
                                          </li>
                                          <li>
                                            <span
                                              class="icon flaticon-money"
                                            ></span>
                                            3 333 333 so'mdan
                                          </li>
                                        </ul>
                                        <ul class="job-other-info">
                                          <li class="time">Yarim ish kuni</li>
                                          <li class="privacy">
                                            Tajriba: Talab qilinmaydi
                                          </li>
                                        </ul>
                                        <div class="btn-box mt-2">
                                          <a
                                            id="showContact"
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
                                  <h4>Информация</h4>
                                  ✅ Требования:<br />
                                  - Опыт работы от 2х лет.<br />
                                  -Знания русского языка.<br /><br />
                                  ✅ Talablar:<br />
                                  -Знания русского языка.<br />
                                  -Знания русского языка.<br /><br />
                                  ✅ Shartlar:<br />
                                  -Знания русского языка.<br />
                                  -Знания русского языка.<br /><br />
                                </div>
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
    <form class="default-form navigation_form">
      <div class="row">
        <div class="form-group d-flex">
          <label for=""></label>
          <div class="btn-box mt-5 ml-4">
            <a
              @click="prevStep"
              class="theme-btn btn-style-five btn_prev ml-1"
              style="
                width: 145px;
                height: 45px;
                color: #343338;
                font-size: 18px;
              "
              ><span class="btn-title">Назад</span></a
            >
            <a
              @click="nextStep"
              class="theme-btn btn-style-two btn_next"
              style="
                width: 145px;
                height: 45px;
                color: #343338;
                font-size: 18px;
                margin-left: 15px;
              "
              ><span class="btn-title">Продолжить</span></a
            >
            <a
              href="#"
              class="theme-btn btn-style-two btn_post d-none"
              style="
                width: 145px;
                height: 45px;
                color: #343338;
                font-size: 18px;
              "
              ><span class="btn-title">Опубликовать</span></a
            >
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<script>

export default {

  methods: {
    nextStep() {
      this.$emit("next-step")
    },
    prevStep() {
      this.$emit("prev-step")
    }
  }
};
</script>

