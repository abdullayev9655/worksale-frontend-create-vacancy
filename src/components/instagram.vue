<template>
  <div class="instagram-card text-left shadow-sm mb-5 bg-white">
    <div>
      <div>
        <div class="d-flex">
          <div class="col-sm-6 d-flex p-2 mt-1">
            <img class="avatar" src="/images/resource/ava.jpg" />
            <h6 class="pt-3 ml-2">worksaleuz</h6>
          </div>
          <div class="col-sm-6 d-flex p-2 mt-3 justify-content-end">
            <svg
              aria-label="Дополнительно"
              class="_8-yf5"
              color="#262626"
              fill="#262626"
              height="24"
              role="img"
              viewBox="0 0 24 24"
              width="24"
            >
              <circle cx="12" cy="12" r="1.5"></circle>
              <circle cx="6" cy="12" r="1.5"></circle>
              <circle cx="18" cy="12" r="1.5"></circle>
            </svg>
          </div>
        </div>
      </div>
      <img class="img-fluid mt-2" :src="'data:image/jpeg;base64,'+details.imageBase64" />
    </div>
    <div class="div p-1">
      <div class="d-flex fontsize mt-1">
        <div class="col-sm-6 d-flex p-1">
          <span class="mr-3">
            <svg
              aria-label="Нравится"
              class="_8-yf5"
              color="#262626"
              fill="#262626"
              height="24"
              role="img"
              viewBox="0 0 24 24"
              width="24"
            >
              <path
                d="M16.792 3.904A4.989 4.989 0 0121.5 9.122c0 3.072-2.652 4.959-5.197 7.222-2.512 2.243-3.865 3.469-4.303 3.752-.477-.309-2.143-1.823-4.303-3.752C5.141 14.072 2.5 12.167 2.5 9.122a4.989 4.989 0 014.708-5.218 4.21 4.21 0 013.675 1.941c.84 1.175.98 1.763 1.12 1.763s.278-.588 1.11-1.766a4.17 4.17 0 013.679-1.938m0-2a6.04 6.04 0 00-4.797 2.127 6.052 6.052 0 00-4.787-2.127A6.985 6.985 0 00.5 9.122c0 3.61 2.55 5.827 5.015 7.97.283.246.569.494.853.747l1.027.918a44.998 44.998 0 003.518 3.018 2 2 0 002.174 0 45.263 45.263 0 003.626-3.115l.922-.824c.293-.26.59-.519.885-.774 2.334-2.025 4.98-4.32 4.98-7.94a6.985 6.985 0 00-6.708-7.218z"
              ></path>
            </svg>
          </span>
          <span class="mr-3">
            <svg
              aria-label="Комментировать"
              class="_8-yf5"
              color="#262626"
              fill="#262626"
              height="24"
              role="img"
              viewBox="0 0 24 24"
              width="24"
            >
              <path
                d="M20.656 17.008a9.993 9.993 0 10-3.59 3.615L22 22z"
                fill="none"
                stroke="currentColor"
                stroke-linejoin="round"
                stroke-width="2"
              ></path>
            </svg>
          </span>
          <span class="mr-3">
            <svg
              aria-label="Поделиться публикацией"
              class="_8-yf5"
              color="#262626"
              fill="#262626"
              height="24"
              role="img"
              viewBox="0 0 24 24"
              width="24"
            >
              <line
                fill="none"
                stroke="currentColor"
                stroke-linejoin="round"
                stroke-width="2"
                x1="22"
                x2="9.218"
                y1="3"
                y2="10.083"
              ></line>
              <polygon
                fill="none"
                points="11.698 20.334 22 3.001 2 3.001 9.218 10.084 11.698 20.334"
                stroke="currentColor"
                stroke-linejoin="round"
                stroke-width="2"
              ></polygon>
            </svg>
          </span>
        </div>
        <div class="col-sm-6">
          <div class="d-flex justify-content-end margin">
            <svg
              aria-label="Сохранить"
              class="_8-yf5"
              color="#262626"
              fill="#262626"
              height="24"
              role="img"
              viewBox="0 0 24 24"
              width="24"
            >
              <polygon
                fill="none"
                points="20 21 12 13.44 4 21 4 3 20 3 20 21"
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
              ></polygon>
            </svg>
          </div>
        </div>
      </div>
      <p class="marginCust2">Нравится: <strong>worksaleuz</strong><br /></p>
      <p class="fontweight marginCust2" style="font-weight: normal">
        <strong>worksaleuz </strong
        ><a href="https://www.instagram.com/worksaleuz/">#worksaleuz</a><br />
        <pre>{{labels}}</pre>
        <pre>{{description}}</pre>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "instagram",
  props: ['details'],
  computed: {
    labels() {
      return `🏢 Компания: ${this.details.company}\n💰 Зарплата: ${this.details.data.salary}\n🧑🏻‍💻 Вид работы: ${this.details.position}\n\n⏳ Занятость: ${this.details.data.typeOfEmployment.ruName}\n💼 Опыт работы: ${this.details.data.experience.ruName}${this.details.phoneNumber ? '\n☎️ Номер телефона: ' + this.details.phoneNumber.join(', ') : ''}${this.details.tgUsername ? '\n📫 Телеграм: ' + this.details.tgUsername : ''}\n📍 Адрес: ${this.details.data.region.ruName}${', '+this.details.address}\n\n`
    },
    description() {
      let text = this.details.descriptions.map( data => {
        return `✅${data.title}\n${data.description}`
      })
      return text.join('\n\n')
    }
  }
};
</script>

<style scoped>
.instagram-card {
  background: #ffffff;
  border-radius: 1.7rem;
  max-width: 430px;
  padding: 10px 23px 23px 23px;
  border: 1px solid #ecedf2;
}
.avatar {
  height: 50px;
  width: 50px;
  border-radius: 50%;
}

.fa.fa-navicon.iconcss {
  float: right;
  color: red;
  text-align: right;
}

pre {
  font-size: 15px;
  color: #696969;
  margin-bottom: 0;
  line-height: 24px;
  font-family: "Roboto", sans-serif;
  white-space: pre-wrap;       
  white-space: -moz-pre-wrap;  
  white-space: -pre-wrap;      
  white-space: -o-pre-wrap;    
  word-wrap: break-word;      
}

.iconcss {
  font-size: 1.2em;
}
.fontsize2 {
  font-size: 1.2em;
}

.fontsize {
  font-size: 1.4em;
}

.d-flex.justify-content-end.margin {
  margin-right: -0.6em;
}

.date {
  font-size: 0.8em;
  color: #999;
}

.redHeart {
  color: red;
}

.marginCust2 {
  margin-top: 2px;
  margin-bottom: 5px;
}
.marginCust {
  margin-top: 0;
  margin-bottom: 0;
}

.fa.fa-heart.redHeart {
  float: right;
  font-size: 1em;
}
</style>