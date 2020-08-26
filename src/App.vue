<template>
  <div id="app">
    <Naslovnica naslov="SEARCH FOR A MEAL" />

    <b-container>
      <PopisJela />
    </b-container>
  </div>
</template>

<script>
import Naslovnica from './components/Naslovnica'
import PopisJela from './components/PopisJela'

export default {
  name: 'App',
  components: {
    Naslovnica,
    PopisJela,
  }
}
</script>

