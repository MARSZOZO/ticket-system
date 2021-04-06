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
            />
          </div>
          <div class="mb-3">
            <label for="exampleInputPassword1" class="form-label">Email:</label>
            <input
              type="email"
              class="form-control"
              id="exampleInputPassword1"
            />
          </div>
          <div class="mb-3">
            <label for="exampleInputPassword1" class="form-label"
              >Сообщение:</label
            >
            <textarea
              class="form-control"
              id="exampleInputPassword1"
            ></textarea>
          </div>
          <div class="mb-3">
            <label>Тип обращения:</label>
            <select class="form-select" aria-label="Default select example">
							<option selected disabled>Выберите тип обращения</option>
              <option v-for="(item, index) in typeAppealList" :value="item.value" :key="index">{{item.text}}</option>
            </select>
          </div>
          <div class="mb-3">
            <label>Приоритет:</label>
            <select class="form-select">
							<option selected disabled>Выберите приоритет</option>
              <option v-for="(item, index) in priorityList" :value="item.value" :key="index">{{item.text}}</option>
            </select>
          </div>
          <div class="mb-3">
            <label>Статус:</label>
            <select class="form-select" aria-label="Default select example">
							<option selected disabled>Выберите статус</option>
              <option v-for="(item, index) in statusList" :value="item.value" :key="index">{{item.text}}</option>
            </select>
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-success">Создать</button>
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
      priorityList: [
				{ text: 'Низкий', value: '0', selected: false },
        { text: 'Средний', value: '1', selected: false },
        { text: 'Высокий', value: '2', selected: false },
        { text: 'Критический', value: '3', selected: false }
			],
			statusList: [
				{ text: 'Новый', value: '0' },
        { text: 'В обработке', value: '1' },
        { text: 'Отложено', value: '2' },
        { text: 'Закрыто', value: '3' }
			],
			typeAppealList: [
				{ text: 'Жалоба на пользователя', value: '0' },
        { text: 'Жалоба на приложение', value: '1' },
        { text: 'Жалоба на сайт', value: '2' },
        { text: 'Оплата', value: '3' },
        { text: 'Функционал', value: '4' },
        { text: 'Авторизация', value: '5' },
        { text: 'Модерация', value: '6' },
        { text: 'Другое', value: '7' },
			]
    };
  },
};
</script>

<style lang="scss" scoped>
</style>