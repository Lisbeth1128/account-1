<template>
  <Layout class-prefix="layout">
    <NumberPad :value.sync="record.amount" @submit="saveRecordItem" />
    <Tabs :data-source="recordTypeList" :value.sync="record.type" />
    <div class="notes">
      <FormItem
        field-name="备注"
        placeholder="在这里输入备注"
        @update:value="onUpdateFormItem"
      />
    </div>
    <Tags/>
  </Layout>
</template>

<script lang="ts">

import Vue from "vue";
import NumberPad from "@/components/Money/NumberPad.vue";
import FormItem from "@/components/Money/FormItem.vue";
import Tags from "@/components/Money/Tags.vue";
import { Component } from "vue-property-decorator";
import Tabs from "@/components/Tabs.vue";
import recordTypeList from "@/constants/recordTypeList";



@Component({
  components: {
    NumberPad,
    FormItem,
    Tags,
    Tabs
  }
})
export default class Money extends Vue {
    record: RecordItem = {
    tags: [],
    notes: "",
    type: "-",
    amount: 0,
  };

  get recordList() {
    return this.$store.state.recordList
  }

  recordTypeList = recordTypeList

  created(){
    this.$store.commit('fetchRecords')
  }

  onUpdateFormItem(value: string) {
    this.record.notes = value;
  }

  saveRecordItem() {
    this.$store.commit('createRecord', this.record)
    if(this.$store.state.createRecordError === null){
      window.alert('已保存')
    }
  }

}
</script>

<style lang="scss">
.layout-content {
  display: flex;
  flex-direction: column-reverse;
}

.notes {
  padding: 12px 0;
}
</style>
