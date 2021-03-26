---
title: "Parameter 'props' implicitly has an 'any' type"
date: 2021-03-26T10:36:28+08:00
draft: true
---

1. 添加两个interface Props & State
2. 类继承React.Component的时候添加类型 React.Component<Props, State>
3. 构造方法中的props添加类型 constructor(props: Props)

```jsx
interface Props {
}

interface State {
}
class Index extends React.Component<Props, State> {

  constructor(props: Props) {
    super(props)
    this.state = {}
  }

  componentDidMount () { }

  render () {

    return (
      <div className=''>
      </div>
    )
  }
}

export default Index
```
