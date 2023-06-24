<template>
  <div class="dropdown1_Container">
    <button class="dropdown1_Button" @click="toggleDropdown">
      {{ selectedItem || "Dropdown example 1" }}
      <img
        v-if="isDropdownVisible"
        class="dropdown1_Icon"
        src="~/assets/icons/arrow-up.svg"
        alt="go up" />
      <img
        v-else
        class="dropdown1_Icon"
        src="~/assets/icons/arrow-bot.svg"
        alt="go down" />
      <ul
        class="dropdown1_List"
        :class="{ show: isDropdownVisible }"
        id="dropdownList">
        <li v-if="shouldShowDropdownExample1" @click="selectItem('')">
          Dropdown example 1
        </li>
        <li @click="selectItem('1 Selected')">1</li>
        <li @click="selectItem('2 Selected')">2</li>
        <li @click="selectItem('3 Selected')">3</li>
        <li @click="selectItem('4 Selected')">4</li>
      </ul>
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isDropdownVisible: false,
      selectedItem: "",
    };
  },
  computed: {
    shouldShowDropdownExample1() {
      return (
        this.selectedItem !== "Dropdown example 1" && this.selectedItem !== ""
      );
    },
  },
  methods: {
    toggleDropdown() {
      this.isDropdownVisible = !this.isDropdownVisible;
    },
    selectItem(item) {
      this.selectedItem = item;
      this.isDropdownVisible = false;
      this.removeDropdownListClass();
    },
    removeDropdownListClass() {
      const dropdownList = document.getElementById("dropdownList");
      dropdownList.classList.remove("show");
    },
  },
};
</script>
