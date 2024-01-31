<template>
 <t-select  style="width: 400px;" v-model:popupVisible="popupVisible" defaultPopupVisible="false"	 clearable  @click="openSealName" v-model="sealName"
    valueType="value" placeholder="请选择" >
    <template #suffixIcon>
      <icon name="form" style="margin-right: 8px; cursor: pointer;" />
    </template>
    <template #empty>
      <div></div>
    </template>      
  </t-select>
  <t-dialog
      v-model:visible="visible"
      header="对话框标题"
      width="40%"
      :confirm-on-enter="true"
      :on-cancel="onCancel"
      :on-esc-keydown="onEscKeydown"
      :on-close-btn-click="onCloseBtnClick"
      :on-overlay-click="onOverlayClick"
      :on-close="close"
      :on-confirm="onConfirmAnother"
    >
      <t-space direction="vertical" style="width: 100%">
        <div>
          <p>这是弹框内容</p>
          <p>This is Dialog Content</p>
        </div>
        <t-pagination v-model="current" v-model:pageSize="pageSize" :total="30" />
      </t-space>
    </t-dialog>
</template>

<script setup lang="ts">
import {
  AddIcon,
  CloudUploadIcon,
  DiscountIcon,
  CloudDownloadIcon,
} from "tdesign-icons-vue-next";
import { ref } from "vue";

import { Icon } from 'tdesign-icons-vue-next';

const popupVisible = ref(false);

const mousedownAction = ()=>{

}

const sealName = ref('');


const visible = ref(false);
const current = ref(1);
const pageSize = ref(10);
const openSealName = ()=>{
  visible.value = true;
}


const onClick = (context:any) => {
  console.log('点击了确认按钮，弹出弹窗', context);
  visible.value = true;
};
const onConfirmAnother = (context:any) => {
  console.log('点击了确认按钮', context);
  visible.value = false;
};
const close = (context:any) => {
  console.log('关闭弹窗，点击关闭按钮、按下ESC、点击蒙层等触发', context);
};
const onCancel = (context:any) => {
  console.log('点击了取消按钮', context);
};
const onEscKeydown = (context:any) => {
  console.log('按下了ESC', context);
};
const onCloseBtnClick = (context:any) => {
  console.log('点击了关闭按钮', context);
};
const onOverlayClick = (context:any) => {
  console.log('点击了蒙层', context);
};

</script>

