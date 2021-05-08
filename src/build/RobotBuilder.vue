<template>
  <div>
    <div class="top-row">
      <div class="top part">
        <img v-bind:src="availableParts.heads[selectedHeadIndex].src" title="head"/>
        <button v-on:click="selectPreviousHead()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextHead()" class="next-selector">&#9658;</button>
      </div>
    </div>
    <div class="middle-row">
      <div class="left part">
        <img v-bind:src="availableParts.arms[selectedLeftArmsIndex].src" title="left arm"/>
        <button v-on:click="selectPreviousLeftArm()" class="prev-selector">&#9650;</button>
        <button v-on:click="selectNextLeftArm()" class="next-selector">&#9660;</button>
      </div>
      <div class="center part">
        <img v-bind:src="availableParts.torsos[selectedTorsosIndex].src" title="left arm"/>
        <button v-on:click="selectPreviousTorsos()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextTorsos()" class="next-selector">&#9658;</button>
      </div>
      <div class="right part">
        <img v-bind:src="availableParts.arms[selectedRightArmsIndex].src" title="left arm"/>
        <button v-on:click="selectPreviousRightArms()" class="prev-selector">&#9650;</button>
        <button v-on:click="selectNextRightArms()" class="next-selector">&#9660;</button>
      </div>
    </div>
    <div class="bottom-row">
      <div class="bottom part">
        <img v-bind:src="availableParts.bases[selectedBasesIndex].src" title="left arm"/>
        <button v-on:click="selectPreviousBases()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextBases()" class="next-selector">&#9658;</button>
      </div>
    </div>
  </div>
</template>

<script>
import availableParts from '../data/parts';

// Line Previous Validation
function getPreviousValidIndex(index, length) {
  const depracatedIndex = index - 1;
  return depracatedIndex < 0 ? length - 1 : depracatedIndex;
}
// Line Next Validation
function getNextValidIndex(index, length) {
  const incrementedIndex = index + 1;
  return incrementedIndex > length - 1 ? 0 : incrementedIndex;
}

export default {
  name: 'RobotBuilder',
  data() {
    return {
      availableParts,
      selectedHeadIndex: 0,
      selectedLeftArmsIndex: 0,
      selectedTorsosIndex: 0,
      selectedRightArmsIndex: 0,
      selectedBasesIndex: 0,
    };
  },
  methods: {
    // Start Top Part
    selectNextHead() {
      this.selectedHeadIndex = getNextValidIndex(
        this.selectedHeadIndex,
        availableParts.heads.length,
      );
    },
    selectPreviousHead() {
      this.selectedHeadIndex = getPreviousValidIndex(
        this.selectedHeadIndex,
        availableParts.heads.length,
      );
    },
    // End Top Part
    // ----------------
    // Start Left Part
    selectNextLeftArm() {
      this.selectedLeftArmsIndex = getNextValidIndex(
        this.selectedLeftArmsIndex,
        availableParts.arms.length,
      );
    },
    selectPreviousLeftArm() {
      this.selectedLeftArmsIndex = getPreviousValidIndex(
        this.selectedLeftArmsIndex,
        availableParts.arms.length,
      );
    },
    // End Left Part
    // ----------------
    // Start Center Part
    selectNextTorsos() {
      this.selectedTorsosIndex = getNextValidIndex(
        this.selectedTorsosIndex,
        availableParts.torsos.length,
      );
    },
    selectPreviousTorsos() {
      this.selectedTorsosIndex = getPreviousValidIndex(
        this.selectedTorsosIndex,
        availableParts.torsos.length,
      );
    },
    // End Center Part
    //-------------------
    // Start Right Part
    selectNextRightArms() {
      this.selectedRightArmsIndex = getNextValidIndex(
        this.selectedRightArmsIndex,
        availableParts.arms.length,
      );
    },
    selectPreviousRightArms() {
      this.selectedRightArmsIndex = getPreviousValidIndex(
        this.selectedRightArmsIndex,
        availableParts.arms.length,
      );
    },
    // End Right Part
    //------------------
    // Start Bottom Part
    selectNextBases() {
      this.selectedBasesIndex = getNextValidIndex(
        this.selectedBasesIndex,
        availableParts.bases.length,
      );
    },
    selectPreviousBases() {
      this.selectedBasesIndex = getPreviousValidIndex(
        this.selectedBasesIndex,
        availableParts.bases.length,
      );
    },
    // End Bottom Part
  },
};
</script>

<style scoped>
.part {
  position: relative;
  width:165px;
  height:165px;
  border: 3px solid #aaa;
}
.part img {
  width:165px;
}
.top-row {
  display:flex;
  justify-content: space-around;
}
.middle-row {
  display:flex;
  justify-content: center;
}
.bottom-row {
  display:flex;
  justify-content: space-around;
  border-top: none;
}
.head {
  border-bottom: none;
}
.left {
  border-right: none;
}
.right {
  border-left: none;
}
.left img {
  transform: rotate(-90deg);
}
.right img {
  transform: rotate(90deg);
}
.bottom {
  border-top: none;
}
.prev-selector {
  position: absolute;
  z-index:1;
  top: -3px;
  left: -28px;
  width: 25px;
  height: 171px;
}
.next-selector {
  position: absolute;
  z-index:1;
  top: -3px;
  right: -28px;
  width: 25px;
  height: 171px;
}
.center .prev-selector, .center .next-selector {
  opacity:0.8;
}
.left .prev-selector {
  top: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.left .next-selector {
  top: auto;
  bottom: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.right .prev-selector {
  top: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  top: auto;
  bottom: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  right: -3px;
}
</style>
