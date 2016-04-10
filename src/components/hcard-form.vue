<template>
    <div>
        <h1>hCard Builder</h1>
        <form v-el:form action="">
            <p class="form-section-title">Personal Details</p>

            <div class="row">
                <div class="medium-6 columns">
                    <label>Given Name
                        <input type="text" name="givenName" id="given-name" v-model="formData.givenName" />
                    </label>
                </div>
                <div class="medium-6 columns">
                    <label>Surname
                        <input type="text" name="surname" id="surname" v-model="formData.surname" />
                    </label>
                </div>
            </div>

            <div class="row">
                <div class="medium-6 columns">
                    <label>Email
                        <input type="email" name="email" id="email" v-model="formData.email" />
                    </label>
                </div>
                <div class="medium-6 columns">
                    <label>Phone
                        <input type="tel" name="phone" id="phone" v-model="formData.phone" />
                    </label>
                </div>
            </div>

            <p class="form-section-title">Address</p>

            <div class="row">
                <div class="medium-6 columns">
                    <label>House Name or #
                        <input type="text" name="houseName" id="house-name" v-model="formData.houseName" />
                    </label>
                </div>
                <div class="medium-6 columns">
                    <label>Street
                        <input type="text" name="street" id="street" v-model="formData.street" />
                    </label>
                </div>
            </div>

            <div class="row">
                <div class="medium-6 columns">
                    <label>Suburb
                        <input type="text" name="suburb" id="suburb" v-model="formData.suburb" />
                    </label>
                </div>
                <div class="medium-6 columns">
                    <label>State
                        <input type="tel" name="state" id="state" v-model="formData.state" />
                    </label>
                </div>
            </div>

            <div class="row">
                <div class="medium-6 columns">
                    <label>Postcode
                        <input type="text" name="postcode" id="postcode" v-model="formData.postcode" />
                    </label>
                </div>
                <div class="medium-6 columns">
                    <label>Country
                        <input type="text" name="country" id="country" v-model="formData.country" />
                    </label>
                </div>
            </div>

            <div class="row cta">
                <div class="medium-6 columns">
                    <input type="file" id="avatar" accept="image/jpeg" v-el:avatar @change="readFile">
                    <button type="button" class="secondary expanded button" @click.prevent="uploadAvatar">Upload Avatar</button>
                </div>
                <div class="medium-6 columns">
                    <button type="button" class="expanded button">Create hCard</button>
                </div>
            </div>
        </form>
    </div>
</template>

<script>
    export default {
        props: ['formData'],
        methods: {
            readFile(e) {
                if ( window.FileReader ) {
                    var input = e.target;
                    if (input.files && input.files[0]) {
                        var reader = new FileReader();
                        var self = this;
                        reader.onload = function (e) {
                            self.formData.avatarDataUrl = e.target.result;
                        }
                        reader.readAsDataURL(input.files[0]);
                    }
                }
            },
            uploadAvatar() {
                this.$els.avatar.click();
            }
        }
    }
</script>

<style lang="sass">
    label {
        text-transform: uppercase;
    }
    input[type="file"] {
        display: none;
    }
    input:invalid {
        border: 1px solid #ff2520;
    }
    .form-section-title {
        font-size: 0.75rem;
        color: #aeaeae;
        border-bottom: 1px solid #aeaeae;
        text-transform: uppercase;
    }
    .cta {
        margin-top: 1rem;
        .button {
            font-size: 1.2rem;
        }
    }
</style>