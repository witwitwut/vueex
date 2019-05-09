<template>
    <div class="alert" :class="colorCode" role="alert" >
        {{message}}
        <button class="close" type="button" data-dismiss="alert" aria-label="close">
            <span aria-hidden="false">X</span>
        </button>
    </div>
</template>

<script>
export default {
    name: 'NotificationMessage',
    props: {
        message: String,
        colorCode: String
    }
}
</script>

<style>

</style>
