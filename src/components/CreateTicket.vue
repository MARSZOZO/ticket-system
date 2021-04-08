<template>
  <div class="modal" id="newTicketModal" tabindex="-1">
    <div class="modal-dialog modal-dialog-centered modal-lg">
      <div class="modal-content">
        <div class="modal-header">
          <h2 class="modal-title text-secondary fw-bold">Новый тикет</h2>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
				<form @submit.prevent="sendData">
        <div class="modal-body">
          <div class="mb-3">
            <label for="exampleInputEmail1" class="form-label text-secondary fw-bold">Имя:</label>
            <input
							required
              type="text"
              class="form-control"
              id="exampleInputEmail1"
              aria-describedby="emailHelp"
							v-model="data.user.name"
            />
          </div>
          <div class="mb-3">
            <label for="exampleInputPassword1" class="form-label text-secondary fw-bold">Email:</label>
            <input
							required
              type="email"
              class="form-control"
              id="exampleInputPassword1"
							v-model="data.user.email"
            />
          </div>
          <div class="mb-3">
            <label for="exampleInputPassword1" class="form-label text-secondary fw-bold"
              >Сообщение:</label
            >
            <textarea
							required
              class="form-control"
              id="exampleInputPassword1"
							v-model="data.body_subject"
            ></textarea>
          </div>
          <div class="mb-3">
            <label class="form-label  text-secondary fw-bold">Тип обращения:</label>
            <select class="form-select" aria-label="Default select example" v-model="data.subject">
              <option v-for="(item, index) in typeAppealList" :value="item.value" :key="index">{{item.text}}</option>
            </select>
          </div>
          <div class="row mb-3">
            <div class="col">
              <label class="form-label  text-secondary fw-bold">Приоритет:</label>
              <select class="form-select" v-model="data.priority">
                <option v-for="(item, index) in priorityList" :value="Number(item.value)" :key="index" :selected="item.selected">{{item.text}}</option>
              </select>
            </div>
            <div class="col">
              <label class="form-label  text-secondary fw-bold">Статус:</label>
              <select class="form-select" aria-label="Default select example" v-model="data.status">
                <option v-for="(item, index) in statusList" :value="Number(item.value)" :key="index" :selected="item.selected">{{item.text}}</option>
              </select>
            </div>
          </div>
        </div>
        <div class="modal-footer">
          <input type="submit" class="btn btn-success me-3 px-4" value="Создать"/>
          <button type="button" class="btn btn-danger px-4" data-bs-dismiss="modal">Отмена</button>
        </div>
				</form>
      </div>
    </div>
  </div>
</template>

<script>
import { Modal } from 'bootstrap'
import moment from 'moment'

function initialState (){
  return {
      modal: null,
			data : {
				user: {
					name: '',
					email: '',
					avatar: ''
				},
				body_subject: null,
				subject: 0,
				status: 0,
				priority: 0,
				ticket_number: null,
				date: moment().format('MM.DD.YYYY, hh:mm'),
			},
      priorityList: [
				{ text: 'Низкий', value: 0},
        { text: 'Средний', value: 1},
        { text: 'Высокий', value: 2},
        { text: 'Критический', value: 3}
			],
			statusList: [
				{ text: 'Новый', value: 0},
        { text: 'В обработке', value: 1},
        { text: 'Отложено', value: 2},
        { text: 'Закрыто', value: 3}
			],
			typeAppealList: [
				{ text: 'Жалоба на пользователя', value: 0 },
        { text: 'Жалоба на приложение', value: 1 },
        { text: 'Жалоба на сайт', value: 2 },
        { text: 'Оплата', value: 3 },
        { text: 'Функционал', value: 4 },
        { text: 'Авторизация', value: 5 },
        { text: 'Модерация', value: 6 },
        { text: 'Другое', value: 7 },
			]
  }
}

export default {
  data() {
    return initialState()
  },
	watch: {
		modal(newValue, oldValue) {
			return new Modal(document.getElementById('newTicketModal'));
		}
	},
  mounted () {
    this.modal = new Modal(document.getElementById('newTicketModal'));
  },

  methods: {
    sendData() {
      this.$emit('createNewTicket', this.data)
      this.modal.hide()
			Object.assign(this.$data, initialState())
    }
  },
};
</script>

<style lang="scss" scoped>
</style>