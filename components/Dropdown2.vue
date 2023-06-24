<template>
  <div class="dropdown2_Container">
    <!-- Bouton -->
    <button class="dropdown2_Button" @click="toggleDropdown">
      {{ selectedItem || "Filtrer par clique" }}
      <!-- Affichage de l'icône correspondante à l'état du menu déroulant -->
      <img
        v-if="!isDropdownVisible"
        class="dropdown2_Icon"
        src="~/assets/icons/arrow-up.svg"
        alt="go up" />
      <img
        v-else
        class="dropdown2_Icon"
        src="~/assets/icons/arrow-bot.svg"
        alt="go down" />
      <!-- Liste du menu déroulant -->
      <ul
        class="dropdown2_List"
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
    toggleDropdown() {
      // Inverse la visibilité du menu déroulant lorsque le bouton est cliqué
      this.isDropdownVisible = !this.isDropdownVisible;
    },
    selectItem(item) {
      // Sélectionne une option dans le menu déroulant
      this.selectedItem = item;
      dropdownList.classList.remove("show"); // Supprime la classe "show" pour masquer la liste du menu déroulant
    },
    removeDropdownListClass() {
      // Supprime la classe "show" pour masquer la liste du menu déroulant
      const dropdownList = document.getElementById("dropdownList");
      dropdownList.classList.remove("show");
    },
  },
};
</script>
