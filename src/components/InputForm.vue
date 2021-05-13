<template>
    <div>
        <b-form @submit="onSubmit" @reset="onReset" v-if="show">
            <b-form-group
                    id="input-group-1"
                    label="Frequency in Mhz:"
                    label-for="input-1"
            >
                <b-form-input
                        id="input-1"
                        v-model="form.frequency"
                        type="email"
                        required
                ></b-form-input>
            </b-form-group>

            <b-form-group id="input-group-2" label="Length in m:" label-for="input-2">
                <b-form-input
                        id="input-2"
                        v-model="form.length"
                        required
                ></b-form-input>
            </b-form-group>

            <b-form-group id="input-group-3" label="Distance of Coil from base in m:" label-for="input-3">
                <b-form-input
                        id="input-3"
                        v-model="form.distanceOfCoilFromBase"
                        required
                ></b-form-input>
                </b-form-group>

            <b-button type="submit" variant="primary">Calculate</b-button>
        </b-form>
        <b-card class="mt-3" header="Form Data Result">
            <pre class="m-0">{{ form }}</pre>
        </b-card>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                form: {
                    frequency: 7,
                    length: 3,
                    distanceOfCoilFromBase: 0,
                },
                show: true
            }
        },
        methods: {
            onSubmit(event) {
                event.preventDefault()
                alert(JSON.stringify(this.form))
            }
        }
    }
</script>