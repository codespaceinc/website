<template>
    <b-container fluid id="contactUsContainer">
        <b-row>
            <b-col cols="12" md="6" class="mb-3">
                <p id="contactUs">CONTACT US</p>
                <p><a class="space-blue" href="tel:+1 786 671 1390">+1 786 671 1390</a></p>
                <div id="socialLinks">
                    <a class="h3 space-blue mr-3" href="https://www.linkedin.com/company/64960637" target="_blank"><b-icon icon="linkedin" /></a>
                    <a class="h3 space-blue mr-3" href="https://github.com/codespaceinc" target="_blank"><b-icon icon="github" /></a>
                    <a class="h3 space-blue mr-3" href="#" target="_blank"><b-icon icon="instagram" /></a>
                </div>
            </b-col>
            <b-col cols="12" md="6">
                <b-form @submit="onSubmit" id="contactForm">
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
                    <b-alert v-model="showSuccessAlert" variant="success" dismissible>
                        Message sent!
                    </b-alert>
                    <b-alert v-model="showFailedAlert" variant="danger" dismissible>
                        Message failed :(
                    </b-alert>
                    <b-button v-if="form.isSending" type="submit" variant="outline-primary">
                        <b-spinner variant="light" small></b-spinner>
                        Sending...
                    </b-button>
                    <b-button v-else type="submit" variant="outline-primary">
                        Send message
                    </b-button>
                </b-form>
            </b-col>
        </b-row>
    </b-container>
</template>

<script>
import emailjs from 'emailjs-com';

export default {
    data() {
        return {
            form: {
                fullName: null,
                email: null,
                message: null,
                isSending: false
            },
            showSuccessAlert: false,
            showFailedAlert: false
        }
    },
    methods: {
      onSubmit(event) {
        event.preventDefault();
        this.form.isSending = true;

        const templateParams = {
            sender_name: this.form.fullName,
            sender_email: this.form.email,
            sender_message: this.form.message
        };

        emailjs.send('default_service', 'contact_form', templateParams, "user_QZI5mBPq12OK9pHLMYqbP")
            .then((response) => {
                console.info('SUCCESS!', response.status, response.text);
                this.showSuccessAlert = true;
                this.form = {
                    fullName: null,
                    email: null,
                    message: null
                }
            }, (err) => {
                this.showFailedAlert = true;
                console.error('Failed to send email...', err);
            })
            .finally(() => this.form.isSending = false)
      }
    }
}
</script>

<style scoped>
    #contactUsContainer {
        margin-bottom: 300px;
    }

    #contactUs {
        font-size: 4em;
        font-weight: 600;
        line-height: 1;
        letter-spacing: 1.17px;
    }

    .form-control {
        color:white;
    }
    
    @media only screen and (max-width: 768px) {
        #contactUsContainer {
            margin-bottom: 200px;
        }
    }

</style>