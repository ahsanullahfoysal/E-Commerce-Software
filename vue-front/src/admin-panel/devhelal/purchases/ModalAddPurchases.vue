<template>
    <div v-if="ShowM" class="modal-mask">
        <div class="modal-wrapper">
            <div class="modal-container">
                <div class="modal-header">
                    <slot name="header">
                        default header
                    </slot>
                </div>
                <div class="modal-body">
                    <slot name="body">
                        default body
                    </slot>
                </div>

                <div class="modal-footer">
                    <slot name="footer">
                        <button class="modal-default-button" @click="modalHide">
                            Close
                        </button>
                    </slot>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import { mapState, mapGetters, mapActions } from 'vuex';
export default {
	data() {
		return {
			
		}
	},
	props: {
        ShowM: Boolean
	},
    methods:{
        modalHide(){
            this.$emit('showfunction', false);
        }
    }

}
</script>

<style scoped>
.modal-mask {
    position: fixed;
    z-index: 9998;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: table;
    transition: opacity 0.3s ease;
}

.modal-wrapper {
    display: flex;
    align-items: center;
    justify-content: flex-end;
}

.modal-container {
    width: 35%;
    height: 100vh;
    margin-right: 0%;
    /* Adjust as needed for your design */
    padding: 10px 10px;
    background-color: #fff;
    border-radius: 2px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
    transition: all 0.3s ease;
    font-family: Helvetica, Arial, sans-serif;
}


.modal-header h3 {
    margin-top: 0;
    color: #42b983;
}

.modal-body {
    margin: 20px 0;
}

.modal-default-button {
    float: right;
}

/* Modal transition styles */
.modal-enter-active, .modal-leave-active {
    transition: opacity 0.3s;
}

.modal-enter, .modal-leave-to /* .modal-leave-active in <2.1.8 */ {
    opacity: 0;
}
</style>