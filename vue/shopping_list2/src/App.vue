<template>
  <div class="header-overall">
    <h1 class="overall-header">Shopping List</h1>
  </div>
  <div v-if="toggleLoginSite" class="LoginSite">
    <h1 class="login-header">Login</h1>
    <p class="login-subheader">E-Mail Address</p>
    <input type="text" v-model="emailAddress" class="list-input" />
    <p class="login-subheader">Password</p>
    <input type="password" v-model="passwordUser" class="list-input" /><br />
    <button class="button-addItem" @click="submitLogin">Login</button>
  </div>

  <div v-if="toggleShoppingList" class="ShoppingList">
    <div class="list-layout">
      <div class="add-Item">
        <p class="addNewItem">Add new Item:</p>
        <input type="text" v-model="newItem" class="list-input" />
      </div>
      <div class="add-quantity">
        <p class="addNewItem">Quantity:</p>
        <input type="text" v-model="quantityItem" class="list-input" />
      </div>
      <button class="button-addItem" @click="addItem">Add Item</button>
    </div>
    <div class="list-layout">
      <ul class="list-itself">
        <h3 v-for="(item, i) in items" :key="i">{{ item.itemName }}</h3>
      </ul>
      <ul class="list-itself">
        <h4 v-for="(item, i) in items" :key="i">{{ item.number }}</h4>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',

  components: {},

  data() {
    return {
      newItem: '',
      quantityItem: '',
      emailAddress: '',
      getEmailAddress: '',
      getPasswordUser: '',
      passwordUser: '',
      toggleLoginSite: true, //set back to true when done
      toggleShoppingList: false, //set back to false when done
      items: [
        {
          id: 1,
          itemName: 'Schokolade',
          number: '3',
        },
        {
          id: 2,
          itemName: 'Milch',
          number: '5',
        },
        {
          id: 3,
          itemName: 'Kekse',
          number: '6',
        },
      ],
    };
  },

  methods: {
    submitLogin() {
      fetch('https://shopping-list-5358b-default-rtdb.europe-west1.firebasedatabase.app/logins.json')
        .then((response) => {
          if (response.ok) {
            return response.json();
          }
        })
        .then((data) => {
          //save data in array
          const results = [];
          for (const id in data) {
            results.push({
              id: id,
              emailAddress: data[id].emailAddress,
              passwordUser: data[id].password,
            });
          }
          for (const count in results) {
            this.getEmailAddress = results[count].emailAddress;
            this.getPasswordUser = results[count].passwordUser;
            if (this.getEmailAddress === this.emailAddress && this.getPasswordUser === this.passwordUser) {
              this.toggleLoginSite = false;
              this.toggleShoppingList = true;
            }
          }
        })
        .catch((error) => {
          console.log('error: ', error);
        });
    },
    addItem() {
      if (this.newItem !== '' && this.quantityItem !== '') {
        this.items.push({ id: 4, itemName: this.newItem, number: this.quantityItem });
      } else {
        alert('You have to type in values for both Item and Quantity!');
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  background-color: #355070;
  display: flex;
  justify-content: center;
}

.LoginSite {
  padding: 2rem 5rem 2rem 5rem;
  align-items: center;
  background-color: #eaac8b;
  border-radius: 2rem;
  max-width: 50rem;
}

.overall-header {
  font-size: 46px;
  color: #e56b6f;
  font-family: Papyrus;
}

.login-header {
  font-family: Papyrus;
}

.login-subheader {
  font-weight: bold;
  font-size: 16px;
  font-family: Papyrus;
}

.addNewItem {
  font-weight: bold;
  font-size: 20px;
  font-family: Papyrus;
}
.list-layout {
  display: flex;
  justify-content: space-around;
}

.add-Item {
  position: relative;
}

.add-quantity {
  position: relative;
}

.button-addItem {
  position: relative;
}
.button-addItem {
  align-self: center;
  background: transparent;
  background-image: none;
  background-position: 0 90%;
  background-repeat: repeat no-repeat;
  background-size: 4px 3px;
  border-radius: 15px 225px 255px 15px 15px 255px 225px 15px;
  border-style: solid;
  border-width: 2px;
  box-shadow: rgba(0, 0, 0, 0.2) 15px 28px 25px -18px;
  box-sizing: border-box;
  color: #41403e;
  cursor: pointer;
  display: inline-block;
  font-family: Papyrus;
  font-weight: bold;
  font-size: 1rem;
  line-height: 23px;
  outline: none;
  padding: 0.75rem;
  text-decoration: none;
  transition: all 235ms ease-in-out;
  border-bottom-left-radius: 15px 255px;
  border-bottom-right-radius: 225px 15px;
  border-top-left-radius: 255px 15px;
  border-top-right-radius: 15px 225px;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.button-addItem:hover {
  box-shadow: rgba(0, 0, 0, 0.3) 2px 8px 8px -5px;
  transform: translate3d(0, 2px, 0);
}

.button-addItem:focus {
  box-shadow: rgba(0, 0, 0, 0.3) 2px 8px 4px -6px;
}

.ShoppingList {
  min-width: 40rem;
  background-color: #eaac8b;
  border-radius: 2rem;
}

.list-input {
  font-family: Papyrus;
  font-weight: bold;
  width: 100%;
  border-radius: 15px;
  border: 2px solid #646464;
  outline: 0;
  font-size: 1.3rem;
  background-color: #6d597a;
  padding: 7px 0;
  color: #e56b6f;
  transition: border-color 0.2s;
}

.list-itself {
  font-family: Papyrus;
  font-weight: bold;
  font-size: 20px;
}
</style>
