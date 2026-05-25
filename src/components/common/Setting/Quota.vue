<script setup lang="ts">
import { NCard, NCol, NRow, NSpace, NStatistic, NTabPane, NTabs } from 'naive-ui'

interface Props {
  userConfig: User.Config
}

const props = defineProps<Props>()
</script>

<template>
  <NSpace vertical>
    <NTabs type="bar" placement="left" animated>
      <NTabPane name="Paid" :tab="$t('setting.paidModel')">
        <div>
          <NCard :title="$t('setting.textChat')">
            <NRow>
              <NCol :span="8">
                <NStatistic
                  :label="$t('setting.todayRequests')"
                  :value="props.userConfig?.quotaCost.paidRequestTimes.todayRequestTimes ?? '-'"
                >
                  <template #suffix>
                    / {{ props.userConfig?.userQuota.requestTimesByDay ?? "-" }}
                  </template>
                </NStatistic>
              </NCol>
              <NCol :span="12">
                <NStatistic :label="$t('setting.todayConsumed')" :value="props.userConfig?.quotaCost.paidTokenCost.todayTokenCost ?? '-'">
                  <template #suffix>
                    / {{ props.userConfig?.userQuota.tokenByDay ?? "-" }}
                  </template>
                </NStatistic>
              </NCol>
            </NRow>
            <NRow>
              <NCol :span="8">
                <NStatistic
                  :label="$t('setting.monthlyRequests')"
                  :value="props.userConfig?.quotaCost.paidRequestTimes.monthRequestTimes ?? '-'"
                >
                  <template #suffix>
                    / {{ props.userConfig?.userQuota.requestTimesByMonth ?? "-" }}
                  </template>
                </NStatistic>
              </NCol>
              <NCol :span="12">
                <NStatistic :label="$t('setting.monthlyConsumed')" :value="props.userConfig?.quotaCost.paidTokenCost.monthTokenCost ?? '-'">
                  <template #suffix>
                    / {{ props.userConfig?.userQuota.tokenByMonth ?? "-" }}
                  </template>
                </NStatistic>
              </NCol>
            </NRow>
          </NCard>

          <NCard :title="$t('setting.imageGeneration')">
            <NRow>
              <NCol :span="8">
                <NStatistic :label="$t('setting.todayImages')" :value="props.userConfig?.quotaCost.paidDrawTimes.todayDrawTimes ?? '-'">
                  <template #suffix>
                    / {{ props.userConfig?.userQuota.drawByDay ?? "-" }}
                  </template>
                </NStatistic>
              </NCol>
            </NRow>
            <NRow>
              <NCol :span="8">
                <NStatistic :label="$t('setting.monthlyImages')" :value="props.userConfig?.quotaCost.paidDrawTimes.monthDrawTimes ?? '-'">
                  <template #suffix>
                    / {{ props.userConfig?.userQuota.drawByMonth ?? "-" }}
                  </template>
                </NStatistic>
              </NCol>
            </NRow>
          </NCard>
        </div>
      </NTabPane>
      <NTabPane name="Free" :tab="$t('setting.freeModel')">
        <div>
          <NCard :title="$t('setting.textChat')">
            <NRow>
              <NCol :span="8">
                <NStatistic
                  :label="$t('setting.todayRequests')"
                  :value="props.userConfig?.quotaCost.freeRequestTimes.todayRequestTimes ?? '-'"
                />
              </NCol>
              <NCol :span="12">
                <NStatistic :label="$t('setting.todayConsumed')" :value="props.userConfig?.quotaCost.freeTokenCost.todayTokenCost ?? '-'" />
              </NCol>
            </NRow>
            <NRow>
              <NCol :span="8">
                <NStatistic
                  :label="$t('setting.monthlyRequests')"
                  :value="props.userConfig?.quotaCost.freeRequestTimes.monthRequestTimes ?? '-'"
                />
              </NCol>
              <NCol :span="12">
                <NStatistic :label="$t('setting.monthlyConsumed')" :value="props.userConfig?.quotaCost.freeTokenCost.monthTokenCost ?? '-'" />
              </NCol>
            </NRow>
          </NCard>
          <NCard :title="$t('setting.imageGeneration')">
            <NRow>
              <NCol :span="8">
                <NStatistic :label="$t('setting.todayImages')" :value="props.userConfig?.quotaCost.freeDrawTimes.todayDrawTimes ?? '-'" />
              </NCol>
            </NRow>
            <NRow>
              <NCol :span="8">
                <NStatistic :label="$t('setting.monthlyImages')" :value="props.userConfig?.quotaCost.freeDrawTimes.monthDrawTimes ?? '-'" />
              </NCol>
            </NRow>
          </NCard>
        </div>
      </NTabPane>
    </NTabs>
  </NSpace>
</template>
