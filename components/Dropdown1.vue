<template>
  <div class="dropdown1_Container">
    <!-- Bouton -->
    <button class="dropdown1_Button" @click="toggleDropdown">
      {{ selectedItem || "Filtrer par clique" }}
      <!-- Affichage de l'icône correspondante à l'état du menu déroulant -->
      <img
        v-if="!isDropdownVisible"
        class="dropdown1_Icon"
        src="~/assets/icons/arrow-up.svg"
        alt="go up" />
      <img
        v-else
        class="dropdown1_Icon"
        src="~/assets/icons/arrow-bot.svg"
        alt="go down" />
      <!-- Liste du menu déroulant -->
      <ul
        class="dropdown1_List"
        :class="{ show: isDropdownVisible }"
        id="dropdownList">
        <!-- Affichage de l'option "Filtrer par clique" si la première option n'est pas sélectionnée -->
        <li v-if="shouldShowDropdownExample1" @click="selectItem('')">
          Filtrer par clique
        </li>
        <!-- Options de base -->
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
      isDropdownVisible: false, // Indique si le menu déroulant est visible ou non
      selectedItem: "", // Option actuellement sélectionnée dans le menu déroulant
    };
  },
  computed: {
    shouldShowDropdownExample1() {
      // Vérifie si l'option "Dropdown example 1" ou aucune option n'est sélectionnée
      return (
        this.selectedItem !== "Dropdown example 1" && this.selectedItem !== ""
      );
    },
  },
  methods: {
    selectItem(item) {
      // Sélectionne une option dans le menu déroulant
      this.selectedItem = item;
      const dropdownList = this.$el.querySelector("#dropdownList");
      dropdownList.classList.remove("show"); // Supprime la classe "show" pour masquer la liste du menu déroulant
    },
    toggleDropdown() {
      this.isDropdownVisible = !this.isDropdownVisible;
      if (this.isDropdownVisible) {
        document.addEventListener("click", this.handleDocumentClick);
      } else {
        document.removeEventListener("click", this.handleDocumentClick);
      }
    },
    handleDocumentClick(event) {
      const dropdownContainer = this.$el.querySelector(".dropdown1_Container");
      if (!dropdownContainer.contains(event.target)) {
        this.isDropdownVisible = false;
      }
    },
  },
};
</script>
