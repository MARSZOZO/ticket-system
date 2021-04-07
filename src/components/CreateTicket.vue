<template>
  <div class="modal fade" id="newTicketModal" tabindex="-1">
    <div class="modal-dialog modal-dialog-centered">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">Новый тикет</h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <div class="mb-3">
            <label for="exampleInputEmail1" class="form-label">Имя:</label>
            <input
              type="text"
              class="form-control"
              id="exampleInputEmail1"
              aria-describedby="emailHelp"
							v-model="data.user.name"
            />
          </div>
          <div class="mb-3">
            <label for="exampleInputPassword1" class="form-label">Email:</label>
            <input
              type="email"
              class="form-control"
              id="exampleInputPassword1"
							v-model="data.user.email"
            />
          </div>
          <div class="mb-3">
            <label for="exampleInputPassword1" class="form-label"
              >Сообщение:</label
            >
            <textarea
              class="form-control"
              id="exampleInputPassword1"
							v-model="data.body_subject"
            ></textarea>
          </div>
          <div class="mb-3">
            <label>Тип обращения:</label>
            <select class="form-select" aria-label="Default select example" v-model="data.subject">
							<option selected disabled>Выберите тип обращения</option>
              <option v-for="(item, index) in typeAppealList" :value="item.value" :key="index">{{item.text}}</option>
            </select>
          </div>
          <div class="mb-3">
            <label>Приоритет:</label>
            <select class="form-select" v-model="data.priority">
							<option selected disabled>Выберите приоритет</option>
              <option v-for="(item, index) in priorityList" :value="Number(item.value)" :key="index">{{item.text}}</option>
            </select>
          </div>
          <div class="mb-3">
            <label>Статус:</label>
            <select class="form-select" aria-label="Default select example" v-model="data.status">
							<option selected disabled>Выберите статус</option>
              <option v-for="(item, index) in statusList" :value="Number(item.value)" :key="index">{{item.text}}</option>
            </select>
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-success" @click="sendData">Создать</button>
          <button type="button" class="btn btn-danger" data-bs-dismiss="modal">Отмена</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
			data : {
				user: {
					name: '',
					email: '',
					avatar: ''
				},
				body_subject: null,
				subject: null,
				status: null,
				priority: null,
				ticket_number: null,
			},
      priorityList: [
				{ text: 'Низкий', value: 0 },
        { text: 'Средний', value: 1 },
        { text: 'Высокий', value: 2 },
        { text: 'Критический', value: 3 }
			],
			statusList: [
				{ text: 'Новый', value: 0 },
        { text: 'В обработке', value: 1 },
        { text: 'Отложено', value: 2 },
        { text: 'Закрыто', value: 3 }
			],
			typeAppealList: [
				{ text: 'Жалоба на пользователя', value: 'Жалоба на пользователя' },
        { text: 'Жалоба на приложение', value: 'Жалоба на приложение' },
        { text: 'Жалоба на сайт', value: 'Жалоба на сайт' },
        { text: 'Оплата', value: 'Оплата' },
        { text: 'Функционал', value: 'Функционал' },
        { text: 'Авторизация', value: 'Авторизация' },
        { text: 'Модерация', value: 'Модерация' },
        { text: 'Другое', value: 'Другое' },
			]
    };
  },
  methods: {
    sendData() {
      this.$emit('createNewTicket', this.data)
			
			if(JSON.parse(localStorage.getItem('ticket')) != null){
				console.log('пустой')
			}

			// localStorage.setItem('ticket', JSON.stringify(this.data))
    }
  },
};
</script>

<style lang="scss" scoped>
</style>