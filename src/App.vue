<template>
  <div
    v-show="submitted"
    class="overflow-hidden bg-dark text-light w-full h-full absolute flex flex-col items-center justify-center"
  >
    <div
      class="w-full flex justify-center flex-col items-center h-full w-full lg:w-[min(120vmin,100%)] px-6 pt-6 md:px-8 md:pt-8 lg:pt-10 lg:px-10 pb-6 md:pb-8 lg:pb-10"
    >
      <div class="grow"></div>
      <span class="text-8xl mb-10">🎉</span>
      <span class="text-xl text-center mb-4"
        >Your request was successfully processed.</span
      >
      <span class="text-4xl text-center mb-10"
        >Thanks for showing some love!</span
      >
      <span
        :onclick="() => (submitted = false)"
        class="clickable cursor-pointer select-none py-2 px-3.5 border-complement border-2 border-solid text-complement font-medium"
        >Go back</span
      >
      <div class="grow flex items-end justify-center">
        <div
          class="flex items-center gap-4 clickable"
          :onclick="() => (submitted = false)"
        >
          <img :src="logo" alt="logo" class="h-8 w-8" />
          <div class="flex self-stretch items-center">
            <span class="text-[24px] leading-none text-white">Chisel</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div
    v-show="!submitted"
    class="overflow-hidden bg-dark text-light w-full h-full absolute flex flex-col items-center justify-center"
  >
    <div
      class="w-full flex justify-center flex-col items-center h-full w-full lg:w-[min(120vmin,100%)] px-6 pt-6 md:px-8 md:pt-8 lg:pt-10 lg:px-10 pb-6 md:pb-8 lg:pb-10"
    >
      <div class="grow"></div>
      <span class="text-8xl mb-10 text-center">⌛</span>
      <span class="text-4xl mb-4 text-center">Coming soon!</span>
      <span class="text-xl mb-4 text-center"
        >We're working on building our beta at the moment.</span
      >
      <iframe class="" id="res" name="res" style="width: 0; height: 0"></iframe>
      <div class="flex flex-col items-center gap-4 mb-20 px-6">
        <iframe
          class=""
          id="res"
          name="res"
          style="width: 0; height: 0"
        ></iframe>
        <div style="display: grid">
          <form
            class="flex items-center"
            action="https://beauty.us14.list-manage.com/subscribe/post?u=eaa7024d4ff006534c1e5b6ee&amp;id=e4cc35834e"
            method="post"
            id="mc-embedded-subscribe-form"
            name="mc-embedded-subscribe-form"
            style="grid-column: 1; grid-row: 1"
            target="res"
          >
            <input
              name="EMAIL"
              id="mce-EMAIL"
              type="email"
              class="outline-none text-dark w-2/3 min-w-[120px] self-stretch items-stretch px-4 border-solid border-2 border-light focus:border-primary"
              placeholder="Your Email"
              :value="email"
            />
            <input
              type="text"
              name="b_eaa7024d4ff006534c1e5b6ee_e4cc35834e"
              tabindex="-1"
              value=""
              style="display: none"
            />
            <div class="grid bg-primary text-white font-medium clickable">
              <input
                class="flex min-w-[max(33.333333,120px) font-medium text-white clickable items-center justify-center px-6 py-3 leading-none bg-primary"
                type="submit"
                value="Subscribe"
                name="subscribe"
                id="mc-embedded-subscribe"
                style="opacity: 0; grid-column: 1; grid-row: 1"
              />
              <div
                class="flex items-center justify-center"
                style="grid-column: 1; grid-row: 1"
              >
                Stay Posted
              </div>
            </div>
          </form>
          <form
            class="flex items-center"
            style="grid-column: 1; grid-row: 1"
            :onsubmit="submit"
          >
            <input
              type="email"
              class="outline-none text-dark w-2/3 min-w-[120px] self-stretch items-stretch px-4 border-solid border-2 border-light focus:border-primary"
              placeholder="Your Email"
              v-model="email"
              required
            />
            <input
              type="text"
              name="b_eaa7024d4ff006534c1e5b6ee_e4cc35834e"
              tabindex="-1"
              value=""
              style="display: none"
            />
            <div class="grid bg-primary text-white font-medium clickable">
              <input
                class="flex min-w-[max(33.333333,120px) font-medium text-white clickable items-center justify-center px-6 py-3 leading-none bg-primary"
                type="submit"
                style="opacity: 0; grid-column: 1; grid-row: 1"
                :disabled="submitting"
                value="Subscribe"
              />
              <div
                class="flex items-center justify-center"
                style="grid-column: 1; grid-row: 1"
              >
                <span style="width: 100%; text-align: center" v-if="!submitting"
                  >Stay Posted</span
                >
                <div
                  v-else
                  style="
                    border-radius: 50%;
                    border-top: 4px solid white;
                    height: 24px;
                    width: 24px;
                    animation: spin 2s linear infinite;
                  "
                ></div>
              </div>
            </div>
          </form>
        </div>
      </div>
      <span
        :onclick="() => navigate('https://chisel.beauty/#roadmap')"
        class="clickable cursor-pointer select-none py-2 px-3.5 border-secondary border-2 border-solid text-secondary font-medium"
        >View Roadmap</span
      >
      <div class="grow flex items-end justify-center">
        <div class="flex items-center gap-4 clickable" :onclick="navigate">
          <img :src="logo" alt="logo" class="h-8 w-8" />
          <div class="flex self-stretch items-center">
            <span class="text-[24px] leading-none text-white">Chisel</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import logo from "./assets/chisel.png";
export default {
  name: "App",
  data() {
    return {
      logo,
      email: "",
      submitted: false,
      submitting: false,
    };
  },
  components: {},
  methods: {
    navigate(href) {
      window.location.href = href;
    },
    submit(e) {
      e.preventDefault();
      this.submitting = true;
      document.getElementById("mc-embedded-subscribe-form").submit();
      const checkAndReport = () => {
        if (document.getElementById("res").contentWindow.document.body) {
          this.submitted = true;
          this.submitting = false;
          setTimeout(() => {
            document.getElementById("res").src = "";
          }, 1000);
          this.email = "";
        } else {
          setTimeout(() => checkAndReport(), 100);
        }
      };
      checkAndReport();
    },
  },
};
</script>

<style>
.clickable {
  user-select: none;
  cursor: pointer;
  transition: 0.1s all linear;
  opacity: 1;
  transform: translate3d(0, 0, 0);
}

.clickable:active {
  opacity: 0.8;
  transform: translate3d(1px, 1px, 0px);
}
</style>
