<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{ sale: theme === 'sale'}">
            <slot>
                default content
            </slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>    
</template>

<script>
export default {
    props:['theme'],
    data() {
        return {

        }
    },
     methods: {
        closeModal() {
            this.$emit('close')
        }
     }
}
</script>

<style scoped>
    .modal{
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: white;
        border-radius: 10px;
    }

    .backdrop{
        top: 0;
        position: fixed;
        background: rgba(0,0,0,0.5);
        width: 100%;
        height: 100%;
    }

    .modal h1 {
        color: rgb(11, 217, 14);
        font-weight: bolder;
        padding: 0;
    }

    .modal p {
        font-style: normal;
    }

    .modal.sale {
        background: rgb(103, 103, 162);
        color: white;
    }

    .modal.sale h1 {
        color: white
    }

    .modal .actions {
        text-align: center;
        margin: 30px 0 10px 0;
    }
    .modal .actions a {
        color: #333;
        padding: 8px;
        border: 1px solid #eee;
        border-radius: 4px;
        text-decoration: none;
        margin: 10px;
    }

    .modal.sale actions{
        color: white;
    }

    .modal.sale actions{
        color: white;
    }

</style>