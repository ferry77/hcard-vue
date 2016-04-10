<template>
    <div class="row h-card-builder">
        <div class="columns small-12 large-6 form">
            <h-card-form :form-data="hCard"></h-card-form>
        </div>
        <div class="columns small-12 large-6 preview">
            <h-card-preview :preview-data="hCard"></h-card-preview>
        </div>
    </div>
</template>

<script>
    import HCardPreview from './components/hcard-preview.vue'
    import HCardForm from './components/hcard-form.vue'

    export default {
        components: {
            HCardPreview,
            HCardForm
        },
        data() {
            return {
                // On larger app, this should be maintain on single state source, ref: vuex
                hCard: {
                    givenName: '',
                    surname: '',
                    email: '',
                    phone: '',
                    houseName: '',
                    street: '',
                    suburb: '',
                    state: '',
                    postcode: '',
                    country: '',
                    avatarDataUrl: ''
                }
            }
        }
    }
</script>


<style lang="sass">

    .form {
        background: #ffffff;
    }
    .preview {
        background: #f2f2f2;
        height: 630px;
    }

</style>