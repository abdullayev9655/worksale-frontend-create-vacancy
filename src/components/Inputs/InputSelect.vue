<template>
  <div class="custom-selected" @blur="onBlurHandler" :tabindex="tabindex">
    <div class="selected d-flex align-items-center position-relative overflow-hidden"  :class="{ open: open, invalid: error }" @click="showItems" >
      <input v-if="open && isSearchable" ref="searchInput" class="form-control rounded-0 position-absolute p-3 searchInput" @blur="onBlurHandler" v-model="searchText" placeholder="Поиск по названия">
      <template v-else-if="selected.hasOwnProperty(itemText)">
        {{ selected[itemText] }}
      </template>
      <template v-else>
        {{placeholder}}
      </template> 
    </div>
    <div class="items" :class="{ selectHide: !open }">
      <div
        v-for="(option, i) of filteredData"
        :key="i"
        @click="
          selected = option;
          searchText = '';
          open = false;
        "
        class="item"
      >
        <p><span>{{option.ruName}}</span></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'InputSelect',
  props: {
    options: {
      type: Array,
      required: true,
    },
    isSearchable: {
      type: Boolean,
      default: false
    },
    default: {
      type: [String, Number],
      default: null,
    },
    tabindex: {
      type: Number,
      default: 0,
    },
    placeholder: {
      type: String,
      default: "Выбрать"
    },
    error: {
      type: Boolean,
      defalut: false
    },
    'item-text': {
      type: String,
      default: 'ruName',
    }
  },
  data() {
    return {
      selected: {},
      open: false,
      searchText: '',
      filteredData: [],
      isTouched: false
    };
  },
  methods: {
    onBlurHandler(event) {
      if(event?.relatedTarget?.tabIndex !== this.tabindex) {
        this.open = false
        this.searchText = ""
      }
    },
    setOptionsToFilteredData() {
      this.filteredData =  [ ...this.options ] 
    },
    setDefaultData() {
      if(!this.isTouched && this.default !== null && this.options.length) {
        this.selected = this.options.find(data => {
          return this.default === data._id
        })
      }
    },
    showItems(){
      this.open = true
      if(!this.isTouched) this.isTouched = true
      if(this.isSearchable) this.$nextTick(() => {
        this.$refs.searchInput.focus()
      })
    }
  },
  watch: {
    searchText() {
      let piece = this.searchText.toUpperCase().split(" ")
      this.filteredData = this.options.filter((item) => {
        let name = item[this.itemText]
        return piece.every(text => {
          name = name.toUpperCase()
          return name.includes(text)
        })
      })
    },
    selected() {
      if(this.isTouched) this.$emit('change', this.selected)
    },
    options() {
      this.setOptionsToFilteredData()
      this.setDefaultData()
    },
  },
  mounted() {
    this.setOptionsToFilteredData()
    this.setDefaultData()
  }
};
</script>

<style scoped>
.custom-selected {
  position: relative;
  width: 100%;
  text-align: left;
  outline: none;
  min-height: 62px;
  line-height: 1.2;
}

.custom-selected .selected {
  background-color: #f0f5f7;
  border-radius: 6px;
  font-weight: 400;
  font-size: 15px;
  border: 1px solid transparent;
  color: #696969;
  padding-left: 1em;
  min-height: 62px;
  cursor: pointer;
  user-select: none;
}

.custom-selected .selected.open {
  border: 1px solid #fde4ad;
  background: white;
  border-radius: 6px 6px 0px 0px;
}
.custom-selected .selected.invalid {
  color: rgba(220, 53, 69, 0.5)
}

.custom-selected .selected:after {
  position: absolute;
  content: "";
  top: 28px;
  right: 1em;
  width: 0;
  height: 0;
  border: 6px solid transparent;
  border-color: #B3B3B3 transparent transparent transparent;
}

.searchInput{
  top: 0; 
  left: 0; 
  border: none; 
  border-radius: 0;
  width: 100%; 
  height: 100%; 
  box-shadow: 0;
}
.searchInput::placeholder{
  color: #cccccc;
}

.custom-selected .items {
  color: #666666;
  border-radius: 0px 0px 6px 6px;
  overflow: hidden;
  border-right: 1px solid #fde4ad;
  border-left: 1px solid #fde4ad;
  border-bottom: 1px solid #fde4ad;
  position: absolute;
  background-color: white;
  max-height: 270px;
  overflow-y: auto;
  left: 0;
  right: 0;
  z-index: 99;
}

.custom-selected .items .input-group-text {
  background: white;
}
.custom-selected .items::-webkit-scrollbar {
  width: 7px;
}
::-webkit-scrollbar-track {
  background: #f1f1f1; 
}
.custom-selected .items::-webkit-scrollbar-thumb {
  background: #f9ab00;
  border-radius: 5px;
}
.custom-selected .items::-webkit-scrollbar-thumb:hover {
  background: #db9602; 
}

.custom-selected .items div.item {
  color: #666666;
  padding-left: 1em;
  cursor: pointer;
  user-select: none;
  background: white;
  transition: background ease 120ms;
}
.custom-selected .items div.item:hover {
  background-color: #f9ab00;
}
.custom-selected .items div.item:hover p {
  color: white;
}
.custom-selected .items .item {
  border-right: 1px solid #fde4ad;
  font-size: 14px !important;
  padding: 5px 10px;
  margin: 0;
}

.custom-selected .items .item:not(:last-child) {
  border-bottom: 1px solid #fde4ad;
}

.custom-selected .items .item p {
  min-height: 10px;
  margin: 10px 0;
  line-height: 1;
}
.selectHide {
  display: none;
}
</style>
