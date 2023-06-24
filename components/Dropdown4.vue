<template>
  <div class="dropdown4_Container">
    <!-- Bouton -->
    <button
      class="dropdown4_Button"
      @mouseover="isDropdownVisible = true"
      @mouseleave="isDropdownVisible = false">
      {{ selectedItem || "Filtrer par survol" }}
      <!-- Affichage de l'icône correspondante à l'état du menu déroulant -->
      <img
        v-if="!isDropdownVisible"
        class="dropdown4_Icon"
        src="~/assets/icons/arrow-up.svg"
        alt="go up" />
      <img
        v-else
        class="dropdown4_Icon"
        src="~/assets/icons/arrow-bot.svg"
        alt="go down" />
      <!-- Liste du menu déroulant -->
      <ul
        class="dropdown4_List"
        :class="{ show: isDropdownVisible }"
        id="dropdownList"
        @mouseover="isDropdownVisible = true"
        @mouseleave="isDropdownVisible = false">
        <!-- Affichage de l'option "Filtrer par survol" si la première option n'est pas sélectionnée -->
        <li v-if="shouldShowDropdownExample1" @click="selectItem('')">
          Filtrer par survol
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
  },
};
</script>
