<template>
  <q-page class="flex-center">
    <h4 class="q-mt-sm q-mb-none text-primary text-weight-bold text-center" @click="Route('Home')">BakedZoo</h4>
    <h5 class="text-italic q-mt-lg q-mb-lg q-pb-xl text-primary text-weight-regular text-center">Manage Account</h5>

    <!-- ManageAccount stuff -->
    <q-card square class="q-pa-lg q-pt-none shadow-0 transparent">
      <q-card-section class="q-pt-none">
        <q-form class="q-gutter-md">
          <q-input style="font-style: italic;" input-style="font-style: normal;" class="bg-white" square filled clearable v-model="account.email" type="email" label="E-mail"/>
          <q-input style="font-style: italic;" input-style="font-style: normal;" class="bg-white" square filled clearable v-model="account.name" type="text" label="Name"/>

          <q-input style="font-style: italic;" input-style="font-style: normal;" class="bg-white" square filled v-model="account.password" :type="isPwd1 ? 'password' : 'text'" label="Current Password">
            <template v-slot:append>
              <q-icon
                :name="isPwd1 ? 'visibility_off' : 'visibility'"
                class="cursor-pointer"
                @click="isPwd1 = !isPwd1"
              ></q-icon>
            </template>
          </q-input>

          <q-input style="font-style: italic;" input-style="font-style: normal;" class="bg-white" square filled v-model="passwordConfirm" :type="isPwd2 ? 'password' : 'text'" label="New Password">
            <template v-slot:append>
              <q-icon
                :name="isPwd2 ? 'visibility_off' : 'visibility'"
                class="cursor-pointer"
                @click="isPwd2 = !isPwd2"
              ></q-icon>
            </template>
          </q-input>
        </q-form>
      </q-card-section>
      <q-card-actions class="q-px-md q-pt-none q-pb-none">
        <q-space></q-space>
        <q-btn padding="none" unelevated style="border-radius: 12px; font-size: 1.15rem;" class="q-pr-xl q-pl-xl text-weight-bold bg-dark" no-caps label="Confirm" @click="UpdateAccount()"/>
      </q-card-actions>
    </q-card>
    <!-- ManageAccount stuff -->

  </q-page>
</template>

<script>
export default {
  name: 'ManageAccount',
  props: ['account'],
  data () {
    return {
      email: '',
      name: '',
      password: '',
      isPwd1: true,
      passwordConfirm: '',
      isPwd2: true
    }
  },
  methods:{
    ManageAccount()
    {
      if (this.email != '' && this.name != '' && this.password != '' && this.password == this.passwordConfirm)
      {
        this.$emit('IsLoggingIn', true)
        this.$emit('Route', 'home')
      }
    },
    Route(newTab)
    {
      this.$emit('Route', newTab)      
    }
  }
}
</script>
