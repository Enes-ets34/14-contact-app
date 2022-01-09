<template>
  <header class="bg-primary text-light text-center">
    <p class="display-6">Contact App</p>
  </header>
  <div class="container">
    <div class="row">
      <Alert v-if="reqList.length === 0" />
      <div class="col-md-8 mx-auto">
        <div class="card-group">
          <Card
            @delete-item="removeItem(user)"
            @add-contact="addContact(user)"
            v-for="user in reqList"
            :key="user.id"
            :user="user"
          />
        </div>

        <div class="col-12 mt-3 mx-auto">
          <h3 class="text-center" v-if="contactList.length > 0">Bağlantılar</h3>
          <div class="card-group">
            <Card
              v-for="user in contactList"
              :key="user.id"
              :user="user"
              :hasAlreadyLinked="true"
              @delete-contact="deleteItem(user)"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Alert from "@/components/Alert";
import Card from "@/components/Card.vue";

export default {
  name: "App",
  components: {
    Card,
    Alert,
  },
  data() {
    return {
      reqList: [
        {
          id: 1,
          name: "Gokhan Kandemir",
          title: "Senior Software Engineer at PureSOL",
          img:
            "https://media-exp1.licdn.com/dms/image/C5603AQFjWy_2_wMdFw/profile-displayphoto-shrink_200_200/0/1588775326389?e=1646265600&v=beta&t=F-PWoY0eE33qs8IAkbVsZOYkCjgS1qOsdhcjPJDq3w8",
          common: 129,
        },
        {
          id: 2,
          name: "Enes Taha Sarı",
          title: "Software Dev.",
          img:
            "https://media.kommunity.com/avatar/4a8d2c46-ecec-4386-85d3-f18fa176f39e_avatar_5e88a71d3c669.jpg",
          common: 150,
        },
      ],
      contactList: [],
    };
  },
  methods: {
    removeItem(user) {
      this.reqList = this.reqList.filter((i) => i.id !== user.id);
    },
    addContact(user) {
      this.contactList.push(user);
      console.log(this.contactList);
      this.reqList = this.reqList.filter((i) => i.id !== user.id);
    },
    deleteItem(user) {
      this.contactList = this.contactList.filter((i) => i.id !== user.id);
      this.reqList.push({ ...user });
      console.log(user);
    },
  },
};
</script>

<style></style>
