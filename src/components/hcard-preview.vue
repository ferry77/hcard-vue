<template>
    <div class="card-preview">
        <p>HCard Preview</p>
        <div class="card">

            <div class="card-header">
                <div class="photo">
                    <img v-show="previewData.avatarDataUrl" v-bind:src="previewData.avatarDataUrl" alt="avatar">
                </div>
                <h2>{{ fullName }}</h2>
            </div>

            <div class="card-body">

                <dl>
                    <dt>Email</dt>
                    <dd>{{ previewData.email }}</dd>
                    <dt>Phone</dt>
                    <dd>{{ previewData.phone }}</dd>
                    <dt>Address</dt>
                    <dd>{{ addressLine1 }}</dd>
                    <dd class="full">{{ addressLine2 }}</dd>
                    <dt>Postcode</dt>
                    <dd class="short">{{ previewData.postcode }}</dd>
                    <dt>Country</dt>
                    <dd class="short">{{ previewData.country }}</dd>
                </dl>

            </div>

        </div>
    </div>
</template>


<script>
    export default {
        props: ['previewData'],
        computed: {
            fullName() {
                return `${this.previewData.givenName} ${this.previewData.surname}`;
            },
            addressLine1() {
                return `${this.previewData.houseName} ${this.previewData.street}`;
            },
            addressLine2() {
                return (this.previewData.suburb.length && this.previewData.state.length ?
                                `${this.previewData.suburb}, ${this.previewData.state}` :
                                `${this.previewData.suburb} ${this.previewData.state}`.trim()
                );
            }
        }
    }
</script>


<style lang="sass" scoped>
    .card-preview {
        width: 100%;
        max-width: 460px;
        margin: 0 auto;
        position: relative;
        top: 50%;
        transform: translateY(-50%);

        p {
            text-align:right;
            text-transform: uppercase;
            margin-bottom: 0.5rem;
            color: #aeaeae;
        }

        .card {
            position: relative;
            background: #ffffff;
            border-bottom: 2px solid #dddddd;

            .card-header {
                height: 100px;
                background: #465563;
                position: relative;

                h2 {
                    color: #ffffff;
                    position: absolute;
                    left: 1rem;
                    bottom: 0;
                }
                .photo {
                    background: #f2f2f2;
                    width: 85px;
                    height: 110px;
                    border: 2px solid #cccccc;
                    position: absolute;
                    right: 10px;
                    top: 10px;
                }
            }

            .card-body {
                padding: 20px;

                &:after {
                    content: '';
                    display: table;
                    clear: both;
                    height: 0;
                }
                dt {
                    font-size: 0.8rem;
                    line-height: 1.7rem;
                    width: 18%;
                }
                dd {
                    width: 82%;
                }
                dt, dd {
                    padding-top: 0.375rem;
                    font-weight: normal;
                    vertical-align: bottom;
                    margin: 0;
                    height: 2rem;
                    float: left;
                    border-bottom: 1px solid #cccccc;

                    &.full {
                        padding-left: 18%;
                        width: 100%;
                    }
                    &.short {
                        width: 32%;
                    }
                }
            }
        }
    }
</style>