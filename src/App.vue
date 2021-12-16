<template>
  <div class="app">
    <img class="border" :src="src">
    <main class="main">
      <Intro class="main__intro" />
      <div class="main__form">
        <p>Ответь на 6 вопросов, чтобы зарегистрироваться</p>
        <VForm />
      </div>
    </main>
    <img class="border bottom" :src="src">
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {
    Intro: () => import('./components/Intro.vue'),
    VForm: () => import('./components/Form.vue')
  },
  data: () => ({
    src: 'data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4gPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMjAwIiBoZWlnaHQ9IjU4IiB2aWV3Qm94PSIwIDAgMTIwMCA1OCIgZmlsbD0ibm9uZSI+IDxnIG9wYWNpdHk9IjAuOCI+IDxwYXRoIGQ9Ik0wIDFDMTAwLjc0MSAxIDE3Ni4wMTQgMSAyMDEuMDU4IDFIMzU4LjczTDM5NS4yMzggMzUuNUg3ODkuOTQ3TDgyNi40NTUgMUgxMjAwIiBzdHJva2U9IiM2NUI5RjQiIHN0cm9rZS13aWR0aD0iMiI+PC9wYXRoPiA8ZyBmaWx0ZXI9InVybCgjZmlsdGVyMF9kXzY6OSkiPiA8cmVjdCB4PSIzOTUuNzY3IiB5PSIzNC41IiB3aWR0aD0iMzk1Ljc2NyIgaGVpZ2h0PSIyIiBmaWxsPSIjNjVCOUY0Ij48L3JlY3Q+IDxyZWN0IHg9IjM5NS43NjciIHk9IjM0LjUiIHdpZHRoPSIzOTUuNzY3IiBoZWlnaHQ9IjIiIGZpbGw9InVybCgjcGFpbnQwX3JhZGlhbF82OjkpIj48L3JlY3Q+IDwvZz4gPC9nPiA8ZGVmcz4gPGZpbHRlciBpZD0iZmlsdGVyMF9kXzY6OSIgeD0iMzc0Ljc2NyIgeT0iMTMuNSIgd2lkdGg9IjQzNy43NjciIGhlaWdodD0iNDQiIGZpbHRlclVuaXRzPSJ1c2VyU3BhY2VPblVzZSIgY29sb3ItaW50ZXJwb2xhdGlvbi1maWx0ZXJzPSJzUkdCIj4gPGZlRmxvb2QgZmxvb2Qtb3BhY2l0eT0iMCIgcmVzdWx0PSJCYWNrZ3JvdW5kSW1hZ2VGaXgiPjwvZmVGbG9vZD4gPGZlQ29sb3JNYXRyaXggaW49IlNvdXJjZUFscGhhIiB0eXBlPSJtYXRyaXgiIHZhbHVlcz0iMCAwIDAgMCAwIDAgMCAwIDAgMCAwIDAgMCAwIDAgMCAwIDAgMTI3IDAiIHJlc3VsdD0iaGFyZEFscGhhIj48L2ZlQ29sb3JNYXRyaXg+IDxmZU1vcnBob2xvZ3kgcmFkaXVzPSIxIiBvcGVyYXRvcj0iZGlsYXRlIiBpbj0iU291cmNlQWxwaGEiIHJlc3VsdD0iZWZmZWN0MV9kcm9wU2hhZG93XzY6OSI+PC9mZU1vcnBob2xvZ3k+IDxmZU9mZnNldD48L2ZlT2Zmc2V0PiA8ZmVHYXVzc2lhbkJsdXIgc3RkRGV2aWF0aW9uPSIxMCI+PC9mZUdhdXNzaWFuQmx1cj4gPGZlQ29tcG9zaXRlIGluMj0iaGFyZEFscGhhIiBvcGVyYXRvcj0ib3V0Ij48L2ZlQ29tcG9zaXRlPiA8ZmVDb2xvck1hdHJpeCB0eXBlPSJtYXRyaXgiIHZhbHVlcz0iMCAwIDAgMCAwLjcwNDE2NyAwIDAgMCAwIDAuOTQ2NzUgMCAwIDAgMCAxIDAgMCAwIDAuNSAwIj48L2ZlQ29sb3JNYXRyaXg+IDxmZUJsZW5kIG1vZGU9Im5vcm1hbCIgaW4yPSJCYWNrZ3JvdW5kSW1hZ2VGaXgiIHJlc3VsdD0iZWZmZWN0MV9kcm9wU2hhZG93XzY6OSI+PC9mZUJsZW5kPiA8ZmVCbGVuZCBtb2RlPSJub3JtYWwiIGluPSJTb3VyY2VHcmFwaGljIiBpbjI9ImVmZmVjdDFfZHJvcFNoYWRvd182OjkiIHJlc3VsdD0ic2hhcGUiPjwvZmVCbGVuZD4gPC9maWx0ZXI+IDxyYWRpYWxHcmFkaWVudCBpZD0icGFpbnQwX3JhZGlhbF82OjkiIGN4PSIwIiBjeT0iMCIgcj0iMSIgZ3JhZGllbnRVbml0cz0idXNlclNwYWNlT25Vc2UiIGdyYWRpZW50VHJhbnNmb3JtPSJ0cmFuc2xhdGUoNjAxLjA1OCAzNS41KSBzY2FsZSg2Mi45NjMgNDk3OS43NikiPiA8c3RvcCBzdG9wLWNvbG9yPSJ3aGl0ZSI+PC9zdG9wPiA8c3RvcCBvZmZzZXQ9IjEiIHN0b3AtY29sb3I9IndoaXRlIiBzdG9wLW9wYWNpdHk9IjAiPjwvc3RvcD4gPC9yYWRpYWxHcmFkaWVudD4gPC9kZWZzPiA8L3N2Zz4g'
  })
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Play:wght@400;700&display=swap');

html {
  min-height: 100vh;
  height: 1px;
  font-size: 18px;
  font-family: 'Play', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

* {
  box-sizing: border-box;
  margin: 0;
  scrollbar-width: thin;
  scrollbar-color: #8774e1 #17212b;
  scroll-behavior: smooth;
  &::-webkit-scrollbar {
    width: 5px;
  }
  &::-webkit-scrollbar-thumb {
    background-color: #8774e1;
    border-radius: 2.5px;
  }
}

body {
  background: #17212b;
  color: white;
  margin: 0;
  height: 100%;
  padding: 60px 0;
}

h1 {
  font-weight: 700;
}

.app {
  max-width: 1200px;
  margin: auto;
  display: flex;
  flex-direction: column;
  height: 100%;
}

.border {
  max-height: 58px;
  min-height: 30px;
  width: 100%;
  display: block;
  &.bottom {
    transform: rotateX(180deg);
  }
}

.main {
  flex-grow: 1;
  display: flex;
  flex-wrap: wrap;
  > * {
    flex: 0 1 600px;
    margin: 30px auto;
  }
  &__form p {
    text-align: center;
    font-size: 20px;
    margin-bottom: 30px;
  }
}

.country-selector__input, .input-tel__input {
	background: none !important;
	border: none !important;
  border-bottom: 1px solid #ff9e5e !important;
  color: #a7bed3 !important;
  box-shadow: none !important;
}

input {
  outline: none;
}

@media (max-width: 640px) {
  html {
    font-size: 16px;
  }
  h1 {
    text-align: center;
  }
  p, .date {
    text-align: center;
  }
  .main__form, .main__intro {
    margin: 30px 10px;
  }
}
</style>
