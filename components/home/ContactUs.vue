<template>
    <b-container fluid style="margin-bottom:300px">
        <b-row>
            <b-col cols="6">
                <p id="contactUs">CONTACT US</p>
                <p><a class="space-blue" href="tel:+1 786 671 1390">+1 786 671 1390</a></p>
                <div id="socialLinks">
                    <a class="h3 space-blue mr-3" href="https://www.linkedin.com/company/64960637" target="_blank"><b-icon icon="linkedin" /></a>
                    <a class="h3 space-blue mr-3" href="https://github.com/codespaceinc" target="_blank"><b-icon icon="github" /></a>
                    <a class="h3 space-blue mr-3" href="#" target="_blank"><b-icon icon="instagram" /></a>
                </div>
            </b-col>
            <b-col cols="6">
                <b-form @submit="onSubmit">
                    <b-form-group
                        label="Your Name"
                        label-for="fullName">
                        <b-form-input
                            id="fullName"
                            class="bg-transparent"
                            type="text"
                            v-model="form.fullName"
                            placeholder="John Doe"
                            required
                            trim
                        ></b-form-input>
                    </b-form-group>
                    <b-form-group
                        label="Your Email"
                        label-for="email">
                        <b-form-input
                            id="email"
                            class="bg-transparent"
                            type="email"
                            v-model="form.email"
                            placeholder="johndoe@gmail.com"
                            required
                            trim
                        ></b-form-input>
                    </b-form-group>
                    <b-form-group
                        label="Message"
                        label-for="message">
                            <b-form-textarea
                                id="message"
                                class="bg-transparent"
                                v-model="form.message"
                                placeholder="I'd like to get a quote regarding..."
                                rows="3"
                                required
                                trim
                            ></b-form-textarea>
                    </b-form-group>
                    <b-button type="submit" variant="outline-info">Send Message</b-button>
                </b-form>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
export default {
    data() {
        return {
            form: {
                fullName: null,
                email: null,
                message: null
            }
        }
    },
    methods: {
      onSubmit(event) {
        event.preventDefault()
        alert(JSON.stringify(this.form))

        // Reset our form values
        this.form = {
            fullName: null,
            email: null,
            message: null
        }
      }
    }
}
</script>

<style>
    #contactUs {
        font-size: 4em;
        font-weight: 600;
        font-stretch: normal;
        font-style: normal;
        line-height: 1.05;
        letter-spacing: 1.17px;
        text-align: left;
    }
</style>