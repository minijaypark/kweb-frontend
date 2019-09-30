<template>
  <a-form :form="form" @submit="handleSubmit">
    <a-form-item v-bind="formItemLayout" label="E-mail">
      <a-input
        v-decorator="[
          'email',
          {
            rules: [
              {
                type: 'email',
                message: 'The input is not valid E-mail!',
              },
              {
                required: true,
                message: 'Please input your E-mail!',
              },
            ],
          },
        ]"
      />
    </a-form-item>
    <a-form-item v-bind="formItemLayout" label="Password">
      <a-input
        v-decorator="[
          'password',
          {
            rules: [
              {
                required: true,
                message: 'Please input your password!',
              },
              {
                validator: validateToNextPassword,
              },
            ],
          },
        ]"
        type="password"
      />
    </a-form-item>
    <a-form-item v-bind="formItemLayout" label="Confirm Password">
      <a-input
        v-decorator="[
          'confirm',
          {
            rules: [
              {
                required: true,
                message: 'Please confirm your password!',
              },
              {
                validator: compareToFirstPassword,
              },
            ],
          },
        ]"
        type="password"
        @blur="handleConfirmBlur"
      />
    </a-form-item>
    <a-form-item v-bind="formItemLayout">
      <span slot="label">
        Nickname&nbsp;
        <a-tooltip title="What do you want others to call you?">
          <a-icon type="question-circle-o" />
        </a-tooltip>
      </span>
      <a-input
        v-decorator="[
          'nickname',
          {
            rules: [
              {
                required: true,
                message: 'Please input your nickname!',
                whitespace: true,
              },
            ],
          },
        ]"
      />
    </a-form-item>
    <a-form-item v-bind="formItemLayout" label="Habitual Residence">
      <a-cascader
        v-decorator="[
          'residence',
          {
            initialValue: ['zhejiang', 'hangzhou', 'xihu'],
            rules: [
              {
                type: 'array',
                required: true,
                message: 'Please select your habitual residence!',
              },
            ],
          },
        ]"
        :options="residences"
      />
    </a-form-item>
    <a-form-item v-bind="formItemLayout" label="Phone Number">
      <a-input
        v-decorator="[
          'phone',
          {
            rules: [
              { required: true, message: 'Please input your phone number!' },
            ],
          },
        ]"
        style="width: 100%"
      >
        <a-select
          slot="addonBefore"
          v-decorator="['prefix', { initialValue: '86' }]"
          style="width: 70px"
        >
          <a-select-option value="86">
            +86
          </a-select-option>
          <a-select-option value="87">
            +87
          </a-select-option>
        </a-select>
      </a-input>
    </a-form-item>
    <a-form-item v-bind="formItemLayout" label="Website">
      <a-auto-complete
        v-decorator="[
          'website',
          { rules: [{ required: true, message: 'Please input website!' }] },
        ]"
        placeholder="website"
        @change="handleWebsiteChange"
      >
        <template slot="dataSource">
          <a-select-option v-for="website in autoCompleteResult" :key="website">
            {{ website }}
          </a-select-option>
        </template>
        <a-input />
      </a-auto-complete>
    </a-form-item>
    <a-form-item
      v-bind="formItemLayout"
      label="Captcha"
      extra="We must make sure that your are a human."
    >
      <a-row :gutter="8">
        <a-col :span="12">
          <a-input
            v-decorator="[
              'captcha',
              {
                rules: [
                  {
                    required: true,
                    message: 'Please input the captcha you got!',
                  },
                ],
              },
            ]"
          />
        </a-col>
        <a-col :span="12">
          <a-button>Get captcha</a-button>
        </a-col>
      </a-row>
    </a-form-item>
    <a-form-item v-bind="tailFormItemLayout">
      <a-checkbox v-decorator="['agreement', { valuePropName: 'checked' }]">
        I have read the
        <a href="">
          agreement
        </a>
      </a-checkbox>
    </a-form-item>
    <a-form-item v-bind="tailFormItemLayout">
      <a-button type="primary" html-type="submit">
        Register
      </a-button>
    </a-form-item>
  </a-form>
</template>

<script lang="ts">
import Vue from 'vue';
import { ValidateCallback } from 'ant-design-vue/types/form/form';
const residences = [
  {
    value: 'zhejiang',
    label: 'Zhejiang',
    children: [
      {
        value: 'hangzhou',
        label: 'Hangzhou',
        children: [
          {
            value: 'xihu',
            label: 'West Lake',
          },
        ],
      },
    ],
  },
  {
    value: 'jiangsu',
    label: 'Jiangsu',
    children: [
      {
        value: 'nanjing',
        label: 'Nanjing',
        children: [
          {
            value: 'zhonghuamen',
            label: 'Zhong Hua Men',
          },
        ],
      },
    ],
  },
];

export default Vue.extend({
  name: 'sign-up',
  data() {
    return {
      form: this.$form.createForm(this),
      confirmDirty: false,
      residences,
      autoCompleteResult: [] as any[],
      formItemLayout: {
        labelCol: {
          xs: { span: 24 },
          sm: { span: 8 },
        },
        wrapperCol: {
          xs: { span: 24 },
          sm: { span: 16 },
        },
      },
      tailFormItemLayout: {
        wrapperCol: {
          xs: {
            span: 24,
            offset: 0,
          },
          sm: {
            span: 16,
            offset: 8,
          },
        },
      },
    };
  },
  methods: {
    handleSubmit(e: any) {
      e.preventDefault();
      this.form.validateFieldsAndScroll((err: Error[], values: any) => {
        if (!err) {
          console.log('Received values of form: ', values);
        }
      });
    },
    handleConfirmBlur(e: any) {
      const value = e.target.value;
      this.confirmDirty = this.confirmDirty || !!value;
    },
    compareToFirstPassword(rule: any, value: string, callback: any) {
      const form = this.form;
      if (value && value !== form.getFieldValue('password')) {
        callback('Two passwords that you enter is inconsistent!');
      } else {
        callback();
      }
    },
    validateToNextPassword(rule: any, value: string, callback: any) {
      const form = this.form;
      if (value && this.confirmDirty) {
        form.validateFields(['confirm'], { force: true });
      }
      callback();
    },
    handleWebsiteChange(value: string) {
      let autoCompleteResult: any[];
      if (!value) {
        autoCompleteResult = [];
      } else {
        autoCompleteResult = ['.com', '.org', '.net'].map(
          domain => `${value}${domain}`
        );
      }
      this.autoCompleteResult = autoCompleteResult;
    },
  },
});
</script>