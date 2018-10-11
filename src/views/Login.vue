<template>
    <div id="Login">
        <form>
            <label>userName</label>
            <input v-model='userName' type="text">
            
            <button @click.prevent='joinRoom'>Register</button>
        </form>
        <input v-model='peerName' type="text">
        <button @click.prevent='call'>Call</button>
        <div class="col-md-7">
          <div id="videoBig">
              <audio id="audioOutput" autoplay controls muted></audio>
              <!-- <video id="videoOutput" autoplay width="640px" height="480px" poster="img/webrtc.png"></video> -->
          </div>
          <div id="videoSmall">
              <audio id="audioInput" autoplay controls muted></audio>
              <!-- <video id="videoInput" autoplay width="240px" height="180px" poster="img/webrtc.png"></video> -->
          </div>
        </div>
    </div>
</template>

<script>
export default {

    name: 'login',

    data() {
        return {
            userName: '',
            roomName: '',
            peerName:''
        };
    },

    methods: {
        joinRoom() {
            this.$store.dispatch('register', { user: this.userName});
            //alert("Login");
            //this.$store.dispatch('start', { user: this.userName, room: this.roomName });
            //this.$store.commit('updateView', 'chat');
        },
        call(){
            this.$store.dispatch('call', { user: this.userName, peer: this.peerName });
        }

    },

};
</script>
