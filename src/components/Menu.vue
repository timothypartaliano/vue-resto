<template>
  <div class="menu">
    <h1>This is Menu page</h1>
    <div v-for="item in menuItems" :key="item.id" class="menu-item">
      <img :src="item.image" alt="Menu Item" class="menu-item-image">
      <div class="menu-item-details">
        <h2>{{ item.name }}</h2>
        <p>Price: {{ item.price }}</p>
        <p>{{ item.detail }}</p>
        <button @click="editMenuItem(item)">Edit</button>
      </div>
    </div>
    <button @click="addMenuItem">Add Menu Item</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      menuItems: []
    };
  },
  mounted() {
    this.fetchMenuData();
  },
  methods: {
    async fetchMenuData() {
      try {
        const response = await fetch('/data.json');
        const data = await response.json();
        this.menuItems = data.menu;
      } catch (error) {
        console.error('Error fetching menu data:', error);
      }
    },
    addMenuItem() {
      const newItem = {
        id: this.menuItems.length + 1,
        name: 'New Menu Item',
        price: '$0.00',
        detail: 'Description of the new menu item',
        image: 'https://source.unsplash.com/random'
      };
      this.menuItems.push(newItem);
    },
    editMenuItem(item) {
      const updatedItem = {
        ...item,
        name: 'Edited Menu Item',
        price: '$10.99'
      };

      const index = this.menuItems.findIndex(menuItem => menuItem.id === item.id);
      if (index !== -1) {
        this.menuItems.splice(index, 1, updatedItem);
      } else {
        console.error('Item not found in menuItems array');
      }
    }
  }
};
</script>

<style>
.menu {
  margin-top: 70px;
}

.menu-item {
  display: flex;
  margin-bottom: 20px;
}

.menu-item-image {
  width: 150px;
  height: 150px;
  object-fit: cover;
  border-radius: 5px;
  margin-right: 20px;
}

.menu-item-details {
  flex: 1;
}

.menu-item-details h2 {
  margin-top: 0;
}

.menu-item-details p {
  margin: 0;
}
</style>