<template lang="pug">
  <v-app id="app">
    <v-content>
      <v-container>
          <v-card>
            <v-card-title>
              <span class="headline">Generate PassWord</span>
            </v-card-title>
            <v-card-text>
              <v-container grid-list-md>
                <v-layout wrap>
                  <v-flex xs10>
                    <v-slider label="Length" thumb-label max="20" v-model="value1" step="1"></v-slider>
                  </v-flex>
                  <v-flex xs2>
                    <span>{{value1}}</span>
                  </v-flex>
                  <v-flex xs12>
                    <v-text-field label="Special Char" v-model="special_car"></v-text-field>
                  </v-flex>
                  <v-flex xs12>
                      <v-btn color="blue" @click="genPass">Generate</v-btn>
                  </v-flex>
                  <v-flex xs12>
                      <v-text-field label="Result" v-model="result"></v-text-field>
                  </v-flex>
                </v-layout>
              </v-container>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn id="password" color="blue" v-clipboard:copy="result" v-clipboard:success="onCopy" v-clipboard:error="onError">Copy</v-btn>
            </v-card-actions>
          </v-card>
      </v-container>
    </v-content>
  </v-app>
</template>
<script>
export default {
  data: () => ({
    value1: 8,
    special_car: '!@#$%^&*()_+',
    result: '',
    other_char: 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890',
    alertType: 'success'
  }),
  computed: {},
  created () {},
  mounted () {},
  methods: {
    tab () {
    },
    genPass () {
      this.result = ''
      var chars = this.special_car + this.other_char
      for (var i = 0; i < this.value1; i++) {
        this.result += chars.charAt(Math.floor(Math.random() * chars.length))
      }
    },
    onCopy: function (e) {
      console.log('Ok!')
    },
    onError: function (e) {
      console.log('Failed!')
    }
  }
}
</script>
<style lang="scss">

#app{
  min-width: 60vh;
}
span{
  font-size: 20px;
}
</style>
