# 开箱即用的表单以及校验组件

原生的表单校验，只支持有限的正则规则，对于复杂验证需求难以实现

各种第三方表单库，则需要学习额外的规则、范式

使用本组件，则只需要通过 `validate` 告诉 `Input` 组件结果是否正确即可

内置诸如 IPv4\IPv6\Email 等简单校验规则

```
<Form onSubmit={evt => alert("提交成功")}>
  <Input
    placeholder="请输入邮箱"
    type="text"
    value={state.email}
    validate={Input.isEmail}
    onChange={evt => this.setState({ email: evt.target.value })}
    customValidity="请输入正确的邮箱地址"
  />

  <Input
    placeholder="请输入密码，至少8位"
    type="password"
    value={state.password}
    onChange={evt => this.setState({ password: evt.target.value })}
    validate={value => Boolean(value.length > 8)}
    customValidity="密码至少8位"
  />

  <button>提交</button>
</Form>
```

如果由于DOM 结构，需要一个在 Form 外的 button 来触发 submit 行为，则需要使用本库提供的 Button，（修复了 IE 全系列不支持 form attributes）

```
<Form onSubmit={evt => alert("提交成功")} id="form-id">
  <Input
    placeholder="请输入邮箱"
    type="text"
    value={state.email}
    validate={Input.isEmail}
    onChange={evt => this.setState({ email: evt.target.value })}
    customValidity="请输入正确的邮箱地址"
  />

  <Input
    placeholder="请输入密码，至少8位"
    type="password"
    value={state.password}
    onChange={evt => this.setState({ password: evt.target.value })}
    validate={value => Boolean(value.length > 8)}
    customValidity="密码至少8位"
  />


</Form>

<button form="form-id" type="submit">提交</button>
```
