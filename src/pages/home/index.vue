<template>
  <div class="tw-p-4 tw-text-white" :class="mode ? 'tw-bg-black' : ''">
    <div class="tw-flex tw-flex-col tw-flex-col-reverse md:tw-flex-row">
      <div class="tw-flex-1 tw-pr-2">
        <div
          :class="mode ? 'tw-bg-black' : 'tw-bg-white'"
          class="tw-flex tw-flex-1 tw-flex-col md:tw-flex-row tw-sticky tw-top-4 tw-justify-between tw-backdrop-blur-xl tw-items-center tw-z-10 tw-rounded-lg tw-p-2"
        >
          <div>
            <h1 :class="modeStyle[mode].main" class="tw-text-2xl tw-font-bold">
              {{ info.name }}
            </h1>
            <h2
              :class="modeStyle[mode].main"
              class="tw-text-lg tw-text-center md:tw-text-left"
            >
              {{ info.position }}
            </h2>
          </div>
          <div class="tw-space-x-2">
            <v-btn
              v-for="(item, index) in info.social"
              :href="item.href"
              :key="index"
              target="_blank"
              icon
            >
              <v-icon :color="mode ? 'white' : 'black'">
                {{ item.iconUrl }}
              </v-icon>
            </v-btn>
          </div>
        </div>
        <hr class="tw-mt-2" />
        <div class="tw-py-2">
          <div :class="modeStyle[mode].main" class="tw-text-md tw-font-bold">
            Summary
          </div>
          <v-list
            dense
            :dark="mode"
            disabled
            rounded
            max-height="200"
            outlined
            class="tw-my-2"
          >
            <v-list-item-group active-class="pink--text" multiple>
              <template v-for="(item, index) in info.summary">
                <v-list-item :key="index">
                  <template>
                    <v-list-item-content>
                      <div
                        class="tw-flex tw-items-start tw-align-center tw-space-x-2"
                      >
                        <v-icon color="yellow darken-3"> mdi-star </v-icon>
                        <v-list-item-title
                          style="white-space: pre-line !important"
                          v-text="item"
                        ></v-list-item-title>
                      </div>
                    </v-list-item-content>
                  </template>
                </v-list-item>
              </template>
            </v-list-item-group>
          </v-list>
          <div :class="modeStyle[mode].main" class="tw-text-md tw-font-bold">
            Technical skill
          </div>
          <v-list
            dense
            :dark="mode"
            disabled
            rounded
            max-height="400"
            outlined
            class="tw-my-2 tw-w-full"
          >
            <v-list-item-group active-class="pink--text" multiple>
              <template v-for="(item, index) in info.mainSkill">
                <v-list-item :key="index">
                  <template>
                    <v-list-item-content>
                      <div
                        class="tw-flex tw-items-start tw-align-center tw-space-x-2"
                      >
                        <v-icon
                          v-if="index === 0 || index === 1"
                          color="yellow darken-3"
                        >
                          mdi-star
                        </v-icon>
                        <v-icon v-else color="grey lighten-1">
                          mdi-star-outline
                        </v-icon>
                        <v-list-item-title
                          style="white-space: pre-line !important"
                          v-text="item"
                        ></v-list-item-title>
                      </div>
                    </v-list-item-content>
                  </template>
                </v-list-item>
              </template>
            </v-list-item-group>
          </v-list>
        </div>
      </div>
      <div class="tw-p-2">
        <kinesis-container>
          <kinesis-element :strength="4" type="depth">
            <v-img
              src="../../assets/heyday-cool.png"
              width="365"
              class="tw-rounded-b-xl tw-rounded-t-xl c-filter"
            />
          </kinesis-element>
        </kinesis-container>
      </div>
    </div>
    <!--region @Working Experienced-->
    <div
      :class="modeStyle[mode].main"
      class="tw-text-md tw-text-center tw-pl-4 tw-font-bold"
    >
      Working Experienced
    </div>
    <div class="tw-pr-2 md:tw-p-4">
      <v-timeline
        class="tw-w-full"
        align-top
        :dense="windowWidth <= 768"
        :dark="mode"
        :class="mode ? 'tw-bg-black' : ''"
      >
        <v-timeline-item
          v-for="(item, i) in info.time"
          :key="i"
          :color="mode ? 'white' : 'black'"
          small
          :large="i === 0"
          class="tw-mb-4"
        >
          <template v-slot:opposite>
            <span
              :class="modeStyle[mode].main"
              class="font-weight-bold tw-border tw-border-0.5 tw-rounded-lg tw-p-4 tw-whitespace-pre-line tw-text-center"
              v-text="item.year"
            ></span>
          </template>
          <div class="tw-space-y-3">
            <h2
              :class="modeStyle[mode].main"
              class="headline font-weight-light"
            >
              {{ item.company }}
            </h2>
            <span
              v-if="windowWidth < 769"
              :class="modeStyle[mode].second"
              class="font-weight-bold tw-py-0.5 tw-whitespace-pre-line tw-text-center"
              v-text="item.year"
            />
            <div class="tw-space-y-1">
              <div :class="modeStyle[mode].main">
                Position: <b>{{ item.position }}</b>
              </div>
              <div :class="modeStyle[mode].main">
                Project: <b>{{ item.project }}</b>
              </div>
              <div :class="modeStyle[mode].main">Technique:</div>
              <div :class="modeStyle[mode].main">
                <v-list
                  dense
                  :dark="mode"
                  disabled
                  rounded
                  max-height="400"
                  outlined
                  class=""
                >
                  <v-list-item-group active-class="pink--text" multiple>
                    <template v-for="(item, index) in item.technique">
                      <v-list-item :key="index">
                        <template>
                          <v-list-item-content>
                            <div class="tw-flex tw-align-center tw-space-x-2">
                              <v-icon color="yellow darken-3">
                                mdi-star
                              </v-icon>
                              <v-list-item-title
                                style="white-space: pre-line !important"
                                v-text="item"
                              ></v-list-item-title>
                            </div>
                          </v-list-item-content>
                        </template>
                      </v-list-item>
                    </template>
                  </v-list-item-group>
                </v-list>
              </div>
            </div>
          </div>
        </v-timeline-item>
      </v-timeline>
    </div>
    <!--endregion-->
    <!--region @Project-->
    <div
      :class="modeStyle[mode].main"
      class="tw-text-md tw-text-center tw-p-4 tw-font-bold"
    >
      Projects
    </div>
    <swiper class="swiper" :options="swiperOption">
      <swiper-slide
          v-for="(item, index) in info.projects"
          :key="index"
          class="tw-flex tw-flex-col tw-justify-between"
      >
        <div class="tw-flex-1 tw-pt-14 tw-text-left">
          <div class="tw-text-xl">{{ item.name }}</div>
          <div>({{ item.position }})</div>
          <div>Team size: {{ item.size }}</div>
          <div>
            {{item.description}}
          </div>
          <div>
            <hr class="tw-my-4">
            <span
                :class="modeStyle[mode].second"
                class="tw-block"
                v-for="tech in item.techs"
                :key="tech"
            >
              {{ tech }}
            </span>
          </div>
        </div>
        <v-btn
            border
            rounded
            icon
            elevation="6"
            target="_blank"
            :dark="mode"
            :href="item.production"
            class="tw-ml-auto tw-mr-4 tw-mb-4"
        >
          <v-icon :class="modeStyle[mode].main" class="tw-animate-pulse"> mdi-arrow-right </v-icon>
        </v-btn>
      </swiper-slide>
    </swiper>
    <!--endregion-->
    <!--region @Footer-->
    <div
      class="tw-fixed tw-flex tw-justify-between tw-w-full tw-bottom-0 tw-text-xs tw-py-2 tw-px-6"
    >
<!--      <p-->
<!--        :class="mode ? 'tw-text-white' : 'tw-text-black'"-->
<!--        small-->
<!--        href="https://github.com/heydayle"-->
<!--      >-->
<!--        Heyday Lê since 2022-->
<!--      </p>-->
      <v-btn icon class="tw-ml-auto" @click="changeMode">
        <template v-if="mode">
          <svg
            width="16"
            height="16"
            viewBox="0 0 512 512"
            class="tw-animate-fadeInTop100"
          >
            <path
              fill="white"
              d="M152.62 126.77c0-33 4.85-66.35 17.23-94.77C87.54 67.83 32 151.89 32 247.38C32 375.85 136.15 480 264.62 480c95.49 0 179.55-55.54 215.38-137.85c-28.42 12.38-61.8 17.23-94.77 17.23c-128.47 0-232.61-104.14-232.61-232.61Z"
            />
          </svg>
        </template>
        <template v-else>
          <svg
            width="16"
            height="16"
            viewBox="0 0 24 24"
            class="tw-animate-tiktokIn"
          >
            <path
              fill="black"
              d="M11 5V1h2v4Zm6.65 2.75l-1.375-1.375l2.8-2.875l1.4 1.425ZM19 13v-2h4v2Zm-8 10v-4h2v4ZM6.35 7.7L3.5 4.925l1.425-1.4L7.75 6.35Zm12.7 12.8l-2.775-2.875l1.35-1.35l2.85 2.75ZM1 13v-2h4v2Zm3.925 7.5l-1.4-1.425l2.8-2.8l.725.675l.725.7ZM12 18q-2.5 0-4.25-1.75T6 12q0-2.5 1.75-4.25T12 6q2.5 0 4.25 1.75T18 12q0 2.5-1.75 4.25T12 18Z"
            />
          </svg>
        </template>
      </v-btn>
    </div>
    <!--endregion-->
    <div class="tw-flex tw-space-x-2 tw-justify-center">
      <v-btn rounded :dark="mode" @click="showHourChart = true">Chart</v-btn>
      <v-btn rounded :dark="mode" @click="showContact = true">Contact</v-btn>
    </div>
    <!--region @CONTACT-->
    <v-bottom-sheet v-model="showContact">
      <v-sheet class="text-center" height="200px">
        <v-btn
          class="mt-6"
          text
          color="red"
          icon
          @click="showContact = !showContact"
        >
          <v-icon> mdi-close </v-icon>
        </v-btn>
        <div
          v-for="(item, index) in info.contact"
          class="py-1 tw-font-bold tw-uppercase"
          :key="index"
        >
          {{ item }}
        </div>
        <div class="tw-space-x-2">
          <v-btn
            v-for="(item, index) in info.social"
            :href="item.href"
            :key="index"
            target="_blank"
            icon
          >
            <v-icon color="black">
              {{ item.iconUrl }}
            </v-icon>
          </v-btn>
        </div>
      </v-sheet>
    </v-bottom-sheet>
    <!--endregion-->
    <!--region @DIALOG-->
    <v-dialog v-model="showHourChart">
      <v-card :dark="mode" class="tw-p-4">
        <v-card-text class="tw-p-4 tw-m-auto">
          <div class="tw-flex tw-m-auto tw-space-x-4">
            <div v-if="info.chartHtml" v-html="info.chartHtml" />
          </div>
        </v-card-text>
      </v-card>
    </v-dialog>
    <!--endregion-->
    <!--region @CURSOR-->
    <cursor-fx
      :config="cursorConfig"
      color="#118ab2"
      color-hover="#06d6a0"
      outside-size="65px"
      hide-inside
    />
    <!--endregion-->
  </div>
</template>

<script>
//region [IMPORT]
import { KinesisContainer, KinesisElement } from "vue-kinesis";
import { CursorFx } from "@luxdamore/vue-cursor-fx";

import "swiper/swiper-bundle.css";
import Swiper from "../../plugins/swiper";

import info from "../../enums/infomation";
//#endregion
export default {
  components: {
    KinesisContainer,
    KinesisElement,
    CursorFx,
    ...Swiper.components,
  },
  data() {
    return {
      //region [ENUMS]
      info,
      //#endregion
      //region [CursorConfig]
      cursorConfig: {
        lerps: {
          dot: 0,
          circle: 0.2,
          custom: 0.23,
        },
        scale: {
          ratio: 0.18,
          min: 0.5,
          max: 1,
        },
        opacity: 0.8,
      },
      //#endregion
      //region [MODE CONFIG]
      mode: true,
      modeStyle: {
        true: {
          main: "tw-text-white",
          second: "tw-text-gray-400",
        },
        false: {
          main: "tw-text-black",
          second: "tw-text-gray-700",
        },
      },
      //#endregion
      //region [SWIPER CONFIG]
      swiperOption: {
        effect: "cards",
        grabCursor: false,
        centeredSlides: true,
        slidesPerView: "auto",
        // navigation: {
        //   nextEl: ".swiper-button-next",
        //   prevEl: ".swiper-button-prev",
        // },
        pagination: {
          el: ".swiper-pagination",
        },
      },
      //#endregion
      showHourChart: false,
      showContact: false,
      windowWidth: null,
    };
  },
  computed: {},
  created() {},
  mounted() {
    this.windowWidth = window.innerWidth;
    this.$ga.page("/");
  },
  methods: {
    changeMode() {
      this.mode = !this.mode;
      this.$ga.page("/");
    },
  },
};
</script>
<style src="@luxdamore/vue-cursor-fx/dist/CursorFx.css"></style>
