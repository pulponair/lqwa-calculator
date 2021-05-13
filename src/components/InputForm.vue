<template>
    <div>
        <b-form @submit="onSubmit">
            <b-form-group
                    id="input-group-1"
                    label="Frequency in Mhz:"
                    label-for="input-1"
            >
                <b-form-input
                        id="input-1"
                        v-model="form.frequency"
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

        </b-form>
        <b-card class="mt-3" header="Form Data Result">
            <pre class="m-0">{{ form }}</pre>
        </b-card>
        <b-card class="mt-3" header="Computed">
            <pre class="m-0">Wavelength: {{ waveLength }}</pre>
            <pre class="m-0">CoilPropoertion: {{ coilProportion }}</pre>
            <pre class="m-0">coilProportionRelative: {{ coilProportionRelative }}</pre>
            <pre class="m-0">coilOffsetRelative: {{ coilOffsetRelative }}</pre>
        </b-card>
        <b-card class="mt-3" header="Efficeny">
            <pre class="m-0">{{ efficiency }}</pre>
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
                }
            }
        },
        computed: {
            waveLength: function () {
                return 300 / this.form.frequency;
            },
            quarterWaveLength: function() {
                return this.waveLength / 4
            },
            coilProportion: function () {
                return this.quarterWaveLength - this.form.length;
            },
            coilProportionRelative: function () {
                return  this.coilProportion / this.quarterWaveLength;
            },

            coilOffsetRelative: function() {
               return this.form.distanceOfCoilFromBase / this.quarterWaveLength;
            },


            efficiency : function() {
                let offset = Math.PI/2 * this.coilOffsetRelative;
                return 1 - (Math.sin(Math.PI/2 * this.coilProportionRelative + offset) - Math.sin(offset)) ;
            }
        }
    }
</script>