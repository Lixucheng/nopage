# 基本

- layout: default
- order: 0

最简单的用法。

---

## 可执行 DEMO

````js
// import 'babel-polyfill';

import * as Antd from 'antd';
import Form, { FormItem, FormCore, Item, If } from '../src';
import AntdWrapper from '../src/wrapper/antd';
import AntdDialogFormWrapper from '../src/dialog/antd';
const { Input, Select, Checkbox, Radio, Switch, Slider, DatePicker, TimePicker,
  Rate, Cascader, TreeSelect, Upload, Button, Modal, Icon, InputNumber, AutoComplete
} = AntdWrapper(Antd);

const { TextArea } = Input;
const { Group: RadioGroup } = Radio;
const { Group: CheckboxGroup } = Checkbox;

const dataSource = [
  { label: 'optA', value: 'optA'},
  { label: 'optB', value: 'optB'}
];

import './antd.scss';

class PageDemo extends React.Component {
	componentWillMount = () => {
     	window.core = this.core = new FormCore();
  	}
  	setStatus = (status) => {
	    this.core.setGlobalStatus(status);
  }
  
  getValues = () => {
    console.log(this.core.getValues());
  }
  	render() {
          const fileList = [{
            uid: 1,
            name: 'xxx.png',
            status: 'done',
            reponse: 'Server Error 500', // custom error message to show
            url: 'http://www.baidu.com/xxx.png',
          }, {
            uid: 2,
            name: 'yyy.png',
            status: 'done',
            url: 'http://www.baidu.com/yyy.png',
          }, {
            uid: 3,
            name: 'zzz.png',
            status: 'error',
            reponse: 'Server Error 500', // custom error message to show
            url: 'http://www.baidu.com/zzz.png',
          }];

	    return (
	      <Form core={this.core} layout={{ label: 8, control: 16 }}>
	          <FormItem label="input" name="input"><Input placeholder="input holder" /></FormItem>
              <FormItem label="AutoComplete" name="AutoComplete"><AutoComplete placeholder="auto holder" options={dataSource} /></FormItem>
              <FormItem label="TextArea" name="TextArea"><TextArea placeholder="text holder"/></FormItem>
	          <FormItem label="select" name="select"><Select placeholder="select holder" options={dataSource} /></FormItem>
	          <FormItem label="Checkbox" name="Checkbox"><Checkbox >选中</Checkbox></FormItem>
	          <FormItem label="Radio" name="Radio"><Radio >选中</Radio></FormItem>
	          <FormItem label="Switch" name="Switch"><Switch /></FormItem>
	          <FormItem label="CheckboxGroup" name="CheckboxGroup"><CheckboxGroup options={dataSource} /></FormItem>
	          <FormItem label="RadioGroup" name="RadioGroup"><RadioGroup options={dataSource} /></FormItem>
	          <FormItem label="Slider" name="Slider"><Slider /></FormItem>
	          <FormItem label="Rate" name="Rate"><Rate /></FormItem>
            <FormItem label="DatePicker" name="DatePicker"><DatePicker placeholder="date holder"/></FormItem>
            <FormItem label="RangePicker" name="RangePicker"><DatePicker.RangePicker placeholder={["start", "end"]}/></FormItem>

            <FormItem label="MonthPicker" name="MonthPicker"><DatePicker.MonthPicker placeholder="month holder"/></FormItem>
            <FormItem label="WeekPicker" name="WeekPicker"><DatePicker.WeekPicker placeholder="week holder"/></FormItem>
	          <FormItem label="TimePicker" name="TimePicker"><TimePicker placeholder="time holder"/></FormItem>
	          <FormItem label="InputNumber" name="InputNumber"><InputNumber placeholder="number holder"/></FormItem>
	          <FormItem label="Cascader" name="Cascader"><Cascader placeholder="cascader holder" options={dataSource} /></FormItem>
	          <FormItem label="TreeSelect" name="TreeSelect"><TreeSelect placeholder="tree holder" treeData={dataSource} /></FormItem>
	          <FormItem label="Upload" name="Upload" value={fileList}>
                <Upload >
                  <Button>
                      <Icon type="upload" /> Click to Upload
                  </Button>
                </Upload>
              </FormItem>
	          <FormItem label="">
                <div>
                    <Button onClick={this.getValues}>获取值</Button>
                    <Button onClick={this.setStatus.bind(this, 'edit')}>切换编辑态</Button>
                    <Button onClick={this.setStatus.bind(this, 'preview')}>切换预览态</Button>
                    <Button onClick={this.setStatus.bind(this, 'disabled')}>切换禁用态</Button>
                </div>
              </FormItem>

	      </Form>);
  	}
}

ReactDOM.render(<PageDemo />, mountNode);
````

````css
body {
    background-color: #FFF;
}
````