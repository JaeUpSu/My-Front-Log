# MVC Pattern

- 선호 X

<br>
<br>

> 애플리케이션을 상호 연결된 세 부분으로 분리하는 소프트웨어 엔지니어링에 사용되는 디자인 패턴

<br>
<br>

## 주요 부분

<br>

- `Model`

```
데이터 및 비즈니스 로직 처리 정보 요청에 
응답하고 상태를 변경하라는 명령에 응답하며 
정보가 변경되면 이벤트 기반 시스템의 
관찰자에게 알림
```

- `View`

```
정보 표시 처리
```

- `Controller`

```
사용자 상호 작용을 처리하고 모델을 업데이트
```

<br>
<br>

## 사용 예시

<br>

1. `사용자는 어떤 방식으로든 인터페이스와 상호 작용 (ex. 버튼 누르기)`

2. `Controller 는 종종 등록된 처리기 또는 Callback 을 통해 사용자 인터페이스의 입력 이벤트를 처리하고 이벤트를 모델이 이해할 수 있는 적절한 사용자 작업으로 변환`

3. `Model 이 요청된 작업을 수행하고 해당 상태를 업데이트`

4. `View 는 Model 을 직접 쿼리하고 그에 따라 변경 사항을 반영하도록 자체 업데이트`

<br>

> 양방향 데이터 흐름을 허용하므로 모델의 업데이트가 뷰에 영향을 미치고 복잡

<br>
<br>

## CODE

<br>

- Model

```javascript
class TaskModel {
  constructor() {
    this.tasks = []
    this.listeners = []
  }

  addTask(task) {
    this.tasks.push(task)
    this.notifyListeners()
  }

  removeTask(taskId) {
    this.tasks = this.tasks.filter(task => task.id !== taskId)
    this.notifyListeners()
  }

  addListener(listener) {
    this.listeners.push(listener)
  }

  notifyListeners() {
    this.listeners.forEach(listener => listener())
  }
}
```

- View

```javascript
class TaskView {
  constructor(controller, model) {
    this.controller = controller
    this.model = model
    this.model.addListener(() => this.render())
  }

  render() {
    const tasks = this.model.tasks.map(task =>
      `<li>${task.name} <button data-id="${task.id}">Delete</button></li>`
    ).join('')
    document.querySelector('#app').innerHTML = `<ul>${tasks}</ul>`
  }

  init() {
    document.querySelector('#app').addEventListener('click', e => {
      if (e.target.tagName === 'BUTTON') {
        this.controller.removeTask(e.target.dataset.id)
      }
    })
  }
}
```

- Controller

```javascript
class TaskController {
  constructor(model) {
    this.model = model
  }

  addTask(task) {
    this.model.addTask(task)
  }

  removeTask(taskId) {
    this.model.removeTask(taskId)
  }
}
```

- Usage

```javascript
const model = new TaskModel();
const controller = new TaskController(model);
const view = new TaskView(controller, model);
view.init();

controller.addTask({id: 1, name: 'Buy milk'});
controller.addTask({id: 2, name: 'Buy bread'});
```
