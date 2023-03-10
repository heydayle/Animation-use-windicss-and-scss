<template>
  <div class="">
    <div class="tw-bg-pink-200 tw-text-center tw-sticky tw-inset-0 tw-z-10 tw-p-4">
      <h1>Happy birthday</h1>
      <h1 class="tw-font-bold tw-text-4xl">Trần Ngọc Tường Vi</h1>
    </div>
    <KinesisContainer tag="div" class="tw-px-20 tw-py-4 tw-space-y-4 tw-bg-pink-100">
        <div
            v-for="(item, index) in ViImages"
            :key="index"
            class="tw-flex tw-justify-between tw-space-x-2"
            :class="{'tw-flex-row-reverse' : index%2 === 0}"
        >
              <div class="tw-relative">
                <KinesisElement
                    :strength="randomNumber()"
                    :type="'depth'"
                    data-cursor-hover
                >
                  <v-img
                      :src="item.src"
                      class="tw-w-80 tw-h-66 tw-shadow-xl tw-rounded-xl"
                  />
                </KinesisElement>
                <KinesisElement
                    :strength="(index + 10)"
                    type="depth"
                    data-cursor-hover
                >
                  <div
                      class="tw-w-14 tw-h-14 tw--top-8 tw-rounded-full tw-shadow-2xl tw-bg-blue-300 tw-absolute"
                      :class="index%2 === 0 ? 'tw--right-4 ' : 'tw--left-4 '"
                  />
                </KinesisElement>
              </div>
          <div class="tw-whitespace-pre-line tw-flex-1">
            {{item.message}}
          </div>
        </div>
      </KinesisContainer>
  </div>
</template>

<script>

import { KinesisContainer, KinesisElement } from "vue-kinesis";
import { ViImages } from '@/enums/index'
export default {
  name: "index",
  components: {
    KinesisContainer,
    KinesisElement,
  },
  data() {
    return {
      ViImages
    }
  },
  methods: {
    randomNumber() {
      return Math.floor(Math.random()*4)
    }
  }
}
</script>

<style scoped>

</style>