<template>
  <div class="col-sm-3">
    <div class="card m-1 h-100">
      <div class="card-header align-items-center">
        <img
          :src="user.img"
          class="card-img-top img-fluid rounded-circle"
          :alt="user.name"
        />
      </div>
      <div class="card-body text-center">
        <h5 class="card-title text-center m-1">{{ user.name }}</h5>

        <div class="d-flex row">
          <small class="text-muted">{{ user.title }}</small>
          <small>
            <a href="#" class="text-muted"
              >{{ user.common }} ortak bağlantı</a
            ></small
          >
        </div>
      </div>
      <div class="card-footer d-flex justify-content-between align-items-center">
        <button
          v-if="!hasAlreadyLinked"
          @click="addContact(user)"
          class="btn btn-primary btn-sm"
        >
          Bağlantı Kur
        </button>
        <button
          v-if="!hasAlreadyLinked"
          @click="$emit('delete-item', user)"
          class="btn btn-danger btn-sm"
        >
          Yoksay
        </button>
        <button v-else @click="deleteContact(user)" class="btn btn-danger">
          Bağlantıyı Kaldır
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["user", "hasAlreadyLinked"],
  methods: {
    addContact(user) {
      this.$emit("add-contact", user);
      this.hasAlreadyLinked = false;
    },
    deleteContact(user) {
      this.$emit("delete-contact", user);
    },
  },
};
</script>

<style></style>
