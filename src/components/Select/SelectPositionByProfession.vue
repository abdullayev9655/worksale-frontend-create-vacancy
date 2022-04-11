<template>
    <div class="Select position-fixed d-flex justify-content-center align-items-center">
        <div class="block_select">
            <div class="block_select_header">
                <h5 class="font-weight-bold">Кого вы хотите найти?</h5>
                <input
                    type="text"
                    v-model="searchText"
                    placeholder="Поиск по названия"
                />
            </div>
            <div class="block_select_tree">
                <ul>
                    <li v-for="(item, index) of items" :key="index">
                        <span @click="item.showPosition = !item.showPosition" class="profession">
                            <span class="icon_chevron">
                                <svg v-if="!item.showPosition" xmlns="http://www.w3.org/2000/svg" width="12" height="12" fill="currentColor" class="bi bi-chevron-right" viewBox="0 0 16 16">
                                    <path fill-rule="evenodd" d="M4.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L10.293 8 4.646 2.354a.5.5 0 0 1 0-.708z"/>
                                </svg>
                                <svg v-else xmlns="http://www.w3.org/2000/svg" width="12" height="12" fill="currentColor" class="bi bi-chevron-down" viewBox="0 0 16 16">
                                    <path fill-rule="evenodd" d="M1.646 4.646a.5.5 0 0 1 .708 0L8 10.293l5.646-5.647a.5.5 0 0 1 .708.708l-6 6a.5.5 0 0 1-.708 0l-6-6a.5.5 0 0 1 0-.708z"/>
                                </svg> 
                            </span>
                            <span class="ml-2">{{item.ruName}}</span>
                        </span>
                        <ul v-show="item.showPosition">
                            <li v-for="(position, index) of item.positions" :key="index" @click="onSelectHandler(item._id,  position._id)">
                                <span class="radio_btn d-flex align-items-center" :class="{checked: position._id === selected.positionId && item._id === selected.professionId}">{{position.ruName}}</span>
                            </li>
                        </ul>
                    </li>
                </ul>
            </div>
            <div class="block_select_footer">
                <div class="btn-box d-flex justify-content-end">
                    <a
                        class="theme-btn btn-style-five btn_prev mr-2"
                        @click="cancel"
                        style="
                        width: 150px;
                        height: 40px;
                        color: #343338;
                        font-size: 16px;
                        "
                        ><span class="btn-title">Отменить</span></a
                    >
                    <a
                        class="theme-btn btn-style-two btn_next"
                        @click="confirm"
                        style="
                        width: 150px;
                        height: 40px;
                        color: #343338;
                        font-size: 16px;
                        "
                        ><span class="btn-title">Выбрать</span></a
                    >
                </div>
            </div>
        </div>
    </div>    
</template>

<script>
export default {
    name: 'select-position-by-profession',
    props: ['value', 'categories'],
    data() {
        return {
            items: [],
            filteredItems: [],
            searchText: "",
            selected: null,
        }
    },
    watch: {
        searchText() {
            let piece = this.searchText.toUpperCase().split(" ")
            this.filteredItems = this.items.filter((item) => {
                let name = item[this.itemText]
                return piece.every(text => {
                name = name.toUpperCase()
                return name.includes(text)
                })
            })
        },
    },
    methods: {
        onSelectHandler(professionId, positionId) {
            this.selected = {professionId, positionId}
        },
        confirm() {
            this.value.category = this.selected
            this.$emit("hidden")
        },
        cancel() {
            this.$emit("hidden")
        }
    },
    created() {
        this.items = this.categories.map((item) => {
            return {
                _id: item._id,
                ruName: item.ruName,
                positions: item.positions,
                showPosition: item.positions.some(pos => pos._id === this.value.category.positionId && item._id === this.value.category.professionId) ,
            }
        })
        this.filteredItems = [...this.items]
        this.selected = this.value.category
    }
}
</script>

<style scoped>
.Select {
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: rgba(48,50,51,.9);
    z-index: 1000;
    padding: 20px;
}

.block_select {
    overflow-y: scroll;
    background: white;
    display: flex;
    flex-direction: column;
    max-height: 100%;
    max-width: 100%;
    z-index: 1042;
    -webkit-user-select: text;
    user-select: text;
    background-color: #fff;
    box-sizing: border-box;
    box-shadow: 0 10px 15px 0 rgb(48 50 51 / 40%);
    margin: auto;
    padding: 30px;
    overflow: auto;
    border-radius: 6px;
}

.block_select_tree {
    width: 620px;
    height: 423px;
    overflow: auto;
    -webkit-overflow-scrolling: touch;
    flex-grow: 1;
}

.block_select_header {
    width: 0;
    min-width: 100%;
    margin-bottom: 10px;
    flex-shrink: 0;
    overflow-wrap: break-word;
    word-wrap: break-word;
}

.block_select_header input {
    position: relative;
    width: 100%;
    border: 1px solid silver;
    display: block;
    line-height: 30px;
    padding: 5px 15px;
    margin: 20px 0 0;
    font-size: 15px;
    color: #696969;
    background: #f0f5f7;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    border-radius: 8px;
    -webkit-transition: all 300ms ease;
    -o-transition: all 300ms ease;
    transition: all 300ms ease;
}

.block_select_header input:focus {
    border-color: #fde4ad;
    background: #ffffff;
}
.block_select_header input::placeholder {
    color: #cccccc;
}

.block_select_tree ul{
    box-sizing: border-box;
    padding-right: 15px;
    padding-top: 10px;
}

ul li {
    cursor: pointer;
    line-height: 1;
    margin-bottom: 12px;
}
ul li span.profession {
    display: block;
    margin-bottom: 10px;
}
ul li label{
    cursor: pointer;
    margin: 0;
}
ul li input{
    cursor: pointer;
}
li ul {
    padding-top: 0 !important;
    padding-left: 19px;
}
.block_select_tree ul li .radio_btn::before {
    content: '';
    display: inline-block;
    vertical-align: middle;
    box-sizing: border-box;
    width: 16px;
    height: 16px;
    border: 1px solid #babdbf;
    margin-right: 8px;
    border-radius: 50%;
}
.block_select_tree ul li .radio_btn.checked::before {
    border-width: 5px;
    border-color: #f9ab00;
}

.block_select_footer {
    margin-top: 20px;
}
</style>