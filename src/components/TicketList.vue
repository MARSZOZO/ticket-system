<template>
  <button
    type="button"
    class="btn btn-secondary mb-4 mt-3 float-end"
    data-bs-toggle="modal"
    data-bs-target="#newTicketModal"
  >
    Новое обращение
  </button>

  <table class="table table-borderless table-hover text-secondary">
    <thead>
      <tr class="text-uppercase">
        <th scope="col">#</th>
        <th scope="col">Пользователь</th>
        <th scope="col">Обращение</th>
        <th scope="col">Статус</th>
        <th scope="col">Приоритет</th>
        <th scope="col">Дата</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(ticket, index) in data" :key="index">
        <td>
          <span class="badge bg-danger"># {{ ticket.ticket_number }}</span>
        </td>
        <td>
          <img src="@/assets/avatar.jpg" alt="" width="50" height="50" />
          <span>{{ ticket.user.name }}</span>
        </td>
        <td>
          <div class="ticket-message">
            <ul>
              <li>
                <span class="text-secondary">Тип обращения: </span
                ><span class="text-info fw-bold">{{ ticket.subject }}</span>
              </li>
              <li>
                <span class="text-secondary">{{ ticket.body_subject }}</span>
              </li>
            </ul>
          </div>
        </td>
        <td v-html="handlerStatus(ticket.status)"></td>
        <td><span v-html="handlerPriority(ticket.priority)"></span></td>
        <td></td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: {
    data: { type: Array }
  },
  methods: {
    handlerStatus(statusCode) {
      switch (statusCode) {
        case 0:
          return '<i class="fas fa-circle status-new"></i> Новый';
        case 1:
          return '<i class="fas fa-circle status-processing"></i> В обработке';
        case 2:
          return '<i class="fas fa-circle status-postpone"></i> Отложено';
        case 3:
          return '<i class="fas fa-circle status-close"></i> Закрыто';
      }
    },
    handlerPriority(priorityCode) {
      switch (priorityCode) {
        case 0:
          return '<i class="fas fa-exclamation priority-low"></i> Низкий';
        case 1:
          return '<i class="fas fa-exclamation priority-middle"></i> Средний';
        case 2:
          return '<i class="fas fa-exclamation priority-high"></i> Высокий';
        case 3:
          return '<i class="fas fa-exclamation priority-super-high"></i> Критический';
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.ticket-message {
  background: #f6f6f6;
  border-left: 3px solid #989898;
  border-radius: 3px;
  padding: 9px 15px;
}

.ticket-message > ul {
  font-size: 12px;
}

tbody > tr {
  background: white;
  max-height: 75px;
  margin-bottom: 10px;
  border-bottom-width: 5px;
  border-color: #f4f4f4;
  vertical-align: middle;
}

ul {
  padding: 0;
  margin: 0;
}

li {
  list-style-type: none;
}
</style>