<template>
  <div class="person">
    <div class="person__photo">
      <img
        :src="person.picture"
        alt="photo"
      />
    </div>
    <div class="person__info">
      <div class="person__info-name">
        <b>{{ person.name }}</b>
      </div>
      <a class="person__info-email" href="mailto:person.email">
        <emailIcon/>
      </a>
      <div class="person__info-age">
        <b>Возраст:</b> {{ person.age }}
      </div>
      <div class="person__info-dtreg">
        <b>Дата регистрации:</b> {{ formatedDate }}
      </div>
      <div class="person__info-about"><b>О себе:</b> {{ person.about }}</div>
    </div>
  </div>
</template>

<script>
import { format } from "date-fns";
import emailIcon from "@/assets/images/email_black_24dp.svg";

export default {
  props: {
    person: {
      type: Object,
      default: null,
    },
  },
  computed: {
    formatedDate() {
      return format(new Date(this.person.registered), "dd.MM.yyyy hh:mm");
    },
  },
  components: {
    emailIcon
  },
};
</script>

<style scoped>
.person {
  display: grid;
  grid-template-columns: 100px 1fr;
  grid-gap: 15px;
}

.person__photo img {
  width: 100px;
}

.person__info {
  display: grid;
  grid-gap: 8px;
}

.person__info-name {
  margin-bottom: 10px;
  font-size: 20px;
}

.person__info-email {
  display: flex;
  background: #ededed;
  border-radius: 8px;
  padding: 3px;
  width: max-content;
}
</style>
