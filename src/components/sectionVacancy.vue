<template>
  <div class="sectionVacancy" data-anm=".anm">
    <div class="page-wrapper">
      <!-- Preloader -->
      <!-- <div class="preloader"></div> -->
      <!-- End Preloader -->

      <!-- Main Header-->
      <!-- <%- include('../inc/header') -%> -->
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

            <!-- Step by step -->
         <section class="step_by_step d-flex align-items-center">
                <div class="auto-container">
                    <div class="row align-items-center">
                        <div class="col-12">
                            <div class="d-flex align-items-center">
                                <div class="step active" data-step="1">
                                    <span class="step_number">1</span>
                                    <span class="step_text">Главное</span>
                                </div>
                                <span class="line"></span>
                                <div class="step disabled" data-step="2">
                                    <span class="step_number">2</span>
                                    <span class="step_text">Детали</span>
                                </div>
                                <span class="line"></span>
                                <div class="step disabled" data-step="3">
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
                      <form data-step="1" class="step default-form">
                        <div class="row">
                          <!-- Input -->
                          <div class="form-group col-8 d-flex">
                            <label>Должность</label>
                            <input
                              type="text"
                              data-input="position"
                              placeholder="Оператор"
                            />
                          </div>
                          <div class="form-group col-8 d-flex">
                            <label>Компания</label>
                            <input
                              type="text"
                              data-input="company"
                              placeholder="Faktura.uz или OOO SPACE ONLINE GENESIS"
                            />
                          </div>
                          <div class="form-group col-8 d-flex">
                            <label>Специализация</label>
                            <select class="chosen-select">
                              <option
                                disabled
                                selected
                                style="text-decoration: underline"
                              >
                                Выбрать
                              </option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                            </select>
                          </div>
                          <div class="form-group col-8 d-flex">
                            <label class="d-block">Описание</label>
                            <div class="descriptions width-100">
                              <div class="square">
                                <div class="description">
                                  <div class="title d-flex">
                                    <span
                                      class="d-flex justify-content-center align-items-center mx-2"
                                    >
                                      <svg
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
                                      data-input="description[title]"
                                      type="text"
                                      value="Обязанности:"
                                      placeholder="Название пункта..."
                                    />
                                    <button>
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
                                    data-input="description[body]"
                                    placeholder="Информация о вакансия..."
                                  ></textarea>
                                </div>
                                <div class="description">
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
                                      data-input="description[title]"
                                      type="text"
                                      value="Требования:"
                                      placeholder="Название пункта..."
                                    />
                                    <button>
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
                                    data-input="description[body]"
                                    class="mb-4"
                                    placeholder="Информация о вакансия..."
                                  ></textarea>
                                </div>
                                <div class="description">
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
                                      data-input="description[title]"
                                      type="text"
                                      value="Условия:"
                                      placeholder="Название пункта..."
                                    />
                                    <button>
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
                                    data-input="description[body]"
                                    class="mb-4"
                                    placeholder="Информация о вакансия..."
                                  ></textarea>
                                </div>
                              </div>
                              <!-- <textarea class="mb-4" placeholder=""></textarea>
                                                            <textarea class="" placeholder=""></textarea> -->
                              <a
                                href=""
                                class="d-block"
                                id="addNewDescription"
                                style="margin-top: -0.5rem"
                                >+ Добавить пункт
                              </a>
                            </div>
                          </div>
                        </div>
                        <div class="row">
                          <div class="form-group col-10 d-flex">
                            <label class="d-block">Зарплата</label>
                            <div class="salary">
                              <div class="radio-box">
                                <input
                                  type="radio"
                                  data-inputType="radio"
                                  data-input="salary[contract]"
                                  name="typeSalary"
                                  id="contract"
                                />
                                <label for="contract">Договорная</label>
                              </div>
                              <div class="radio-box mt-4">
                                <input
                                  type="radio"
                                  data-input=""
                                  name="typeSalary"
                                  id="salary"
                                  checked=""
                                />
                                <label for="salary">Указать</label>
                              </div>
                              <div class="d-flex" style="margin-top: 27px">
                                <select class="chosen-select">
                                  <option disabled selected>Ежемесячно</option>
                                  <option>Разработчик</option>
                                  <option>Разработчик</option>
                                  <option>Разработчик</option>
                                  <option>Разработчик</option>
                                  <option>Разработчик</option>
                                </select>
                                <label
                                  style="min-width: auto; margin-left: 14px"
                                  >от</label
                                >
                                <input
                                  data-input="salary[from]"
                                  style="margin: 0 14px"
                                  type="text"
                                  placeholder="2 000 000"
                                />
                                <label style="min-width: auto">до</label>
                                <input
                                  data-input="salary[to]"
                                  style="margin: 0 20px 0 14px"
                                  type="text"
                                  placeholder="3 000 000"
                                />
                                <select class="chosen-select">
                                  <option disabled selected>сум</option>
                                  <option>Разработчик</option>
                                  <option>Разработчик</option>
                                  <option>Разработчик</option>
                                  <option>Разработчик</option>
                                  <option>Разработчик</option>
                                </select>
                              </div>
                            </div>
                          </div>
                        </div>
                      </form>
                      <form data-step="2" class="step default-form">
                        <div class="row">
                          <!-- Input -->
                          <div class="form-group col-7 d-flex">
                            <label>Регион</label>
                            <select class="chosen-select">
                              <option
                                disabled
                                selected
                                style="text-decoration: underline"
                              >
                                Выбрать
                              </option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                            </select>
                          </div>
                          <div class="form-group col-7 d-flex">
                            <label>Адрес</label>
                            <input
                              type="text"
                              placeholder="Шайхантахур, улица Зафарабад, 7-дом"
                            />
                          </div>
                          <div class="form-group col-7 d-flex">
                            <label>График работы</label>
                            <select class="chosen-select">
                              <option
                                disabled
                                selected
                                style="text-decoration: underline"
                              >
                                Выбрать
                              </option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                            </select>
                          </div>
                          <div class="form-group col-7 d-flex">
                            <label>Опыт работы</label>
                            <select class="chosen-select">
                              <option
                                disabled
                                selected
                                style="text-decoration: underline"
                              >
                                Выбрать
                              </option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                              <option>Разработчик</option>
                            </select>
                          </div>
                          <div
                            class="form-group col-7 d-flex"
                            style="margin-bottom: 23px"
                          >
                            <label class="d-block">Телефон номер</label>
                            <div class="phone_numbers width-100">
                              <div class="phone_number">
                                <input
                                  type="text"
                                  placeholder="(00) 123-45-67"
                                />
                                <button class="delete_area_phone_number">
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
                              <a
                                href=""
                                class="d-block"
                                id="addNewPhoneNumber"
                                style="margin-top: 10px"
                                >+ Добавить пункт
                              </a>
                            </div>
                          </div>
                          <div class="form-group col-7 d-flex">
                            <label>Телеграм</label>
                            <input
                              type="text"
                              placeholder="@username_telegram"
                            />
                          </div>
                        </div>
                      </form>
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
                      <form class="default-form navigation_form">
                        <div class="row">
                          <div class="form-group col-8 d-flex">
                            <label></label>
                            <div class="btn-box mt-5">
                              <a
                                href="#"
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
                                href="#"
                                class="theme-btn btn-style-two btn_next"
                                style="
                                  width: 145px;
                                  height: 45px;
                                  color: #343338;
                                  font-size: 18px;
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
      <!-- <%- include('../inc/footer') -%> -->
      <!-- End Main Footer -->
    </div>
  </div>
</template>

<script>

export default {
  name: "sectionVacancy",
  components: {},
  data() {
    return {
    };
  },
  methods: {},
};
</script>

<style>
button {
    background-color: transparent;
    outline: none !important;
    cursor: pointer;
    min-width: auto;  
    border: none !important;
}


 .descriptions .description .title {
  position: relative;
}

.descriptions .description .title input{
  border: none !important;
  background: transparent !important;
  height: 40px;
  color: #969696;
  font-weight: 600;
  font-size: 16px;
  padding: 0;
}

.descriptions .description .title input::placeholder{
  font-weight: 400;
}

.descriptions .description .title button{
  margin-right: 5px;
} 

</style>
