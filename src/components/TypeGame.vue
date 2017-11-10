<template>
  <div class="type-game">
    <div>
      <span class="txt matched">{{matched}}</span>
      <span class="txt remaining">{{remaining}}</span>
    </div>
    <input @keydown="onKeydown" @input="onInput" v-model="message" placeholder="type" >
  </div>
</template>

<script>

const TARGETS = [
  'apple',
  'banana',
  'pinapple',
  'strawberry',
  'watermelon',
  'grape',
  'raspberry'
]
function isValid (char) {
  return /[a-zA-Z0-9!? ]/.test(char)
}
function getRandomTarget () {
  const idx = Math.floor(Math.random() * TARGETS.length)
  return TARGETS[idx]
}
export default {
  name: 'TypeGame',
  data () {
    return {
      message: '',
      correct: 'type it'
    }
  },
  computed: {
    matched () {
      const arr = []
      for (let i = 0; i < this.correct.length; i++) {
        const c = this.message[i]
        if (c == null || c !== this.correct[i]) {
          break
        }
        arr.push(c)
      }
      return arr.join('')
    },
    remaining () {
      return this.correct.slice(this.matched.length)
    }
  },
  watch: {
    remaining () {
      if (this.correct.length > 0 && this.remaining.length === 0) {
        this.correct = getRandomTarget()
        this.message = ''
      }
    }
  },
  methods: {
    onInput (event) {
      // do nothing
    },
    onKeydown (event) {
      if (!isValid(event.key)) {
        console.log(event)
        event.preventDefault()
      }
      // do nothing
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.txt {
  margin: 0px;
  padding: 0px;
  font-size: 2em;
}

.matched {
  text-decoration: underline;
  color: red;
}
</style>
