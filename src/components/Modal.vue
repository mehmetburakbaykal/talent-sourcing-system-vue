<template>
    <div v-show="modalActive" class="modal-container">
        <div class="overlay"></div>
        <div class="modal-content">
            <button @click="toggleModal" class="modal-close-btn">
                <i className="fa-solid fa-x fa-xl"></i>
            </button>
            <ul class="modal-inputs">
                <li class="inputs">
                    <label for="name">Name-Surname: </label>
                    <input type="text" v-model="fullName" name="fullName">
                </li>
                <li class="inputs">
                    <label for="name">Phone Number: </label>
                    <input type="text" v-model="phone" name="phone">
                </li>
                <li class="inputs">
                    <label for="name">E-mail Address: </label>
                    <input type="text" v-model="mail" name="mail">
                </li>
                <li class="inputs">
                    <label for="name">Previous Interactions: </label>
                    <select name="interactions" v-model="interactions" id="interactions">
                        <option value="None"></option>
                        <option value="Called">Called</option>
                        <option value="Mail sent">Mail sent</option>
                    </select>
                </li>
                <li class="inputs">
                    <label for="name">Candidate Status: </label>
                    <select name="status" v-model="status" id="status">
                        <option value="None"></option>
                        <option value="Sourced">Sourced</option>
                        <option value="Interviewing">Interviewing</option>
                        <option value="Offer sent">Offer sent</option>
                        <option value="Hired">Hired</option>
                    </select>
                </li>
                <li className="submit-btn">
                    <input @click="onSubmit" type="submit" name="submit" value="Submit" />
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "Modal",
    props: {
        modalActive: Boolean,
        toggleModal: Function,
        candidates: Array,
    },
    data() {
        return {
            fullName: '',
            phone: '',
            mail: '',
            interactions: '',
            status: ''
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault();

            if (!this.fullName) {
                alert('Please add a name-surname');
                return;
            } else if (!this.phone) {
                alert('Please add a phone number');
                return;
            } else if (!this.mail) {
                alert('Please add a mail address');
                return;
            }

            const newCandidate = {
                // id: Math.floor(Math.random * 10000),
                fullName: this.fullName,
                phone: this.phone,
                mail: this.mail,
                interactions: this.interactions,
                status: this.status
            }

            this.$emit('add-candidate', newCandidate);

            this.toggleModal();

            this.fullName = '';
            this.phone = '';
            this.mail = '';
            this.interactions = '';
            this.status = '';
        }
    }
}
</script>

<style>
.modal-container,
.overlay {
    width: 100vw;
    height: 100vh;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    position: fixed;
}

.overlay {
    background-color: rgba(49, 49, 49, 0.8);
}

.modal-content {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: absolute;
    top: 40%;
    left: 50%;
    transform: translate(-50%, -50%);
    line-height: 1.4;
    background-color: #f1f1f1;
    min-width: 25%;
    min-height: 40%;
}

.modal-inputs>li {
    margin-bottom: 5%;
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.modal-close-btn {
    position: absolute;
    top: 5px;
    right: 5px;
    border: none;
    cursor: pointer;
}

.submit-btn {
    margin-top: 10%;
}
</style>