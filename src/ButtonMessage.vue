<template>
  <div class="sc-message--button" :style="messageColors">
    <p class="sc-message--button--text" v-linkified>
      <span v-html="data.text"></span>
    </p>

    <template v-if="data.buttons.length">
      <div class="sc-message--button--buttons">
        <button v-for="button in data.buttons" @click="_handleClick(button)">{{button.text}}</button>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
      required: true
    },
    message: {
      type: Object,
      required: true
    },
    messageColors: {
      type: Object,
      required: true
    },
    onButtonClick: {
      type: Function,
      required: true
    }
  },
  methods: {
    _handleClick (button) {
      this.onButtonClick(button, this.message)
    }
  }
}
</script>

<style scoped>
.sc-message--button {
  background: #eaeaea;
  border-radius: 6px;
  padding: 0 12px;
  max-width: calc(100% - 40px);
}

.sc-message--button .sc-message--button--buttons {
  padding-bottom: 5px;
}

.sc-message--button button {
  cursor: pointer;
  color: white;
  background-color: #4e8cff;
  border-radius: 30px;
  border: none;
  font-size: 14px;
  padding: 12px 17px;
  margin: 0 10px 10px 0;
}

.sc-message--button button:hover {
  background-color: blue;
}

.sc-message--button button:last-child {
  margin-right: 0;
}

.sc-message--button .sc-message--button--text {
  font-weight: 400;
  font-size: 14px;
  line-height: 1.4;
  white-space: pre-wrap;
  word-wrap: break-word;
  -webkit-font-smoothing: subpixel-antialiased;
}
</style>
