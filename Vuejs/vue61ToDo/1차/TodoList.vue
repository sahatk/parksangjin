<style scoped>
ul {
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
}
li {
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
}
li.checked {
    background: #bbb;
    color: #fff;
    text-decoration: line-through;
}
.checkBtn {
    line-height: 45px;
    color: #62acde;
    margin-right: 5px;
}
.removeBtn {
    margin-left: auto;
    color: #de4343;
}

.list-enter-active,
.list-leave-active {
    transition: all 1s;
}
.list-enter,
.list-leave-to {
    opacity: 0;
    transform: translateY(30px);
}
</style>

<template>
    <section>
        <transition-group name="list" tag="ul">
            <li
                v-for="(todoItem, index) in todoItems"
                v-bind:key="todoItem.id"
                v-bind:class="checked(todoItem.done)"
                v-on:click="doneToggle(todoItem.id)"
            >
                <i class="checkBtn fas fa-check" aria-hidden="true"></i>
                {{ todoItem.todo }}
                <span
                    class="removeBtn"
                    type="button"
                    v-on:click="removeTodo(todoItem.id)"
                >
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </transition-group>
    </section>
</template>

