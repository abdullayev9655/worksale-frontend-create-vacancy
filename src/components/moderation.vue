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
                    <div class="moderation">
                      <div class="moderationText">
                        <h2>Ваша вакансия отправлена на модерацию!</h2>
                        <p class="descriptionMod">
                          Процесс модерации займет некоторое время.<br />После
                          проверки с вами свяжутся наши специалисты!
                        </p>
                      </div>
                      <div class="boxMod">
                        <div class="ModTitle">
                          <h4>
                            Ваша вакансия будет опубликована в
                            <span style="font-weight: bold"
                              >3 разных источниках,</span
                            >
                            подпишитесь что бы не простить публикацию
                          </h4>
                        </div>
                        <div class="lineMod"></div>
                        <div class="icons-b">
                          <div class="row">
                            <div
                              class="col-lg-4 col-md-4 col-sm-4 col-12 mtop-sm"
                            >
                              <div class="center-b">
                                <div
                                  class="d-flex flex-column align-items-center"
                                >
                                  <img src="../assets/images/instagram.png" alt="" />
                                  <p class="mb-0 titleIcons">Instagram</p>
                                </div>
                                <a
                                  href="https://www.instagram.com/worksaleuz/"
                                  target="_blank"
                                  >Подписаться</a
                                >
                              </div>
                            </div>
                            <div
                              class="col-lg-4 col-md-4 col-sm-4 col-12 mtop-sm"
                            >
                              <div class="center-b">
                                <div
                                  class="d-flex flex-column align-items-center"
                                >
                                  <img src="../assets/images/telegram.png" alt="" />
                                  <p class="mb-0 titleIcons">Telegram</p>
                                </div>
                                <a
                                  href="https://t.me/worksaleuz"
                                  target="_blank"
                                  >Подписаться</a
                                >
                              </div>
                            </div>
                            <div
                              class="
                                col-lg-4 col-md-4 col-sm-4 col-12
                                mtop-sm
                                m-auto
                              "
                            >
                              <div class="center-b">
                                <div
                                  class="d-flex flex-column align-items-center"
                                >
                                  <img src="../assets/images/Site.png" alt="" />
                                  <p class="mb-0 titleIcons">Сайт</p>
                                </div>
                                <a href="/" target="_blank">Перейти</a>
                              </div>
                            </div>
                          </div>
                        </div>
                        <div class="btns-b">
                          <form class="default-form navigation_form">
                            <div class="row d-flex justify-content-center">
                              <div class="form-group d-flex">
                                <!-- <div class="mt-5 mediaBtnBoxSm">
                                  <a
                                    @click="prevStep"
                                    class="
                                      theme-btn
                                      btn-style-five
                                      mediaButtonsSm
                                      btn_prev
                                      ml-1
                                    "
                                    style="
                                      width: 180px;
                                      height: 45px;
                                      color: #343338;
                                      font-size: 18px;
                                    "
                                    ><span class="btn-title fsz-14"
                                      >На главную</span
                                    ></a
                                  >
                                  <a
                                    @click="nextStep"
                                    class="
                                      theme-btn
                                      btn-style-two
                                      mediaButtonsSm
                                    "
                                    style="
                                      width: 180px;
                                      height: 45px;
                                      color: #343338;
                                      font-size: 18px;
                                      margin-left: 15px;
                                    "
                                    ><span class="btn-title fsz-14"
                                      >Добавить еще</span
                                    ></a
                                  >
                                </div> -->
                                <div class="btn-box mediaBtnBoxSm mt-5">
                                  <a
                                    @click="goToMain"
                                    class="theme-btn btn-style-five btn_prev"
                                    style="
                                      width: 150px !important;
                                      height: 49px !important;
                                      color: #343338;
                                      font-size: 18px;
                                    "
                                    ><span class="btn-title"
                                      >На главную</span
                                    ></a
                                  >
                                  <a
                                    @click="reloadPage"
                                    class="theme-btn btn-style-two btn_next"
                                    style="
                                      width: 236px !important;
                                      height: 49px !important;
                                      color: #343338;
                                      font-size: 18px;
                                      margin-left: 7px;
                                    "
                                    ><span class="btn-title"
                                      >Разместить вакансию</span
                                    ></a
                                  >
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
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  methods: {
    reloadPage() {
      location.reload();
    },
    goToMain() {
      location.href = "/";
    },
  },
};
</script>

<style scoped>
.center-b {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.moderation .moderationText {
  margin: 0 auto 40px;
}

.moderation .moderationText h2 {
  font-size: 30px;
  font-weight: 500;
  line-height: 35px;
  color: #4a4a4a;
  text-align: center;
}
.moderation .moderationText .descriptionMod {
  font-weight: 300 !important;
  font-size: 18px;
  line-height: 23px;
  text-align: center;
  color: #4a4a4a;
  width: 533px;
  margin: 15px auto 10px;
}

.moderation .boxMod {
  width: 700px;
  height: auto;
  margin: 40px auto;
  background: #ffffff;
  box-shadow: 0px 0px 50px 5px rgba(167, 167, 167, 0.25);
  border-radius: 20px;
  padding: 30px 80px;
}

.moderation .boxMod .ModTitle h4 {
  font-weight: 300;
  font-size: 16px;
  line-height: 21px;
  text-align: center;
  color: #4a4a4a;
  margin: 0px auto;
}

.lineMod {
  width: 95%;
  height: 1px;
  background: #f3f2f2;
  margin: 35px auto;
}

.center-b .titleIcons {
  font-weight: 400;
  font-size: 16px;
  margin: 5px auto;
  line-height: 25px;
  text-align: center;
  color: #4a4a4a;
}
.fsz-14 {
  font-size: 14px !important;
}
</style>

