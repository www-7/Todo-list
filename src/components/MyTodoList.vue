<template>
    <div class="todo">
        <div class="list">
            <input class="checked" type="checkbox">
            <span class="text">{{ title }}</span>
        </div>
        <div>
            <button class="delette btn"><img src="/src/assets/Pencil.png" alt=""></button>
            <button class="edit btn"><img src="/src/assets/delete.png" alt=""></button>
        </div>
    </div>
</template>

<script>
export default {
    props: ['title'],
    data() {
        return {
          text: ''
        }
    }
}
</script>

<style scoped>
.todo {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 390px;
    height: 40px;
    border: 1px solid #E1E1E1
}
.delette {
    background: #0085FF;
}
.edit {
    background: #FF0000;
}
.btn {
    margin-right: 10px;
    width: 20px;
    height: 20px;
    border-radius: 5px;
    border: none;
}

</style>