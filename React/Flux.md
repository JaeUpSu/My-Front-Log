# Flux Pattern

<br>
<br>


> Facebook 이 React 로 작업할 때 내부적으로 사용하는 아키텍처

> 단방향 데이터 흐름을 활용하여 React 의 구성 가능한 뷰 구성요소를 보완

<br>
<br>

## 주요 부분

<br>

- `Dispatcher`

```
Flux 애플리케이션의 모든 데이터 흐름을 
관리하는 일종의 글로벌 허브

본질적으로 Stores 에 대한 Callback Registory 이며 자체 정보 존재 X
```

- `Stores`

```
여기에는 응용 프로그램의 상태 및 논리가 포함

전통적인 MVC의 모델과 다소 유사하지만 
단일 데이터 행에 해당하는 것이 아니라 
많은 개체의 상태를 관리
```

- `Action`

```
"Type" 속성과 일부 데이터를 
포함하는 간단한 개체

앱에서 어떤 일이 발생하면 작업이 발송
```

- `View`

```
React를 사용하여 작성
Store 가 업데이트되면 다시 렌더링
```

<br>
<br>

## 사용 예시

<br>

1. `사용자는 React View 와 상호 작용`

2. `View 는 중앙 Dispatcher 를 통해 Application 데이터 및 비즈니스 로직을 보유하는 다양한 Stores 로 Action 을 전파`

3. `각 Store 가 변겨되면 변경을 알리는 이벤트를 방송`

4. `View 는 이러한 이벤트를 수신하고 Stores 에서 새 데이터를 검색 후 다음 View 를 업데이트`

<br>

> 단방향 데이터 흐름은 애플리케이션을 보다 예측 가능하고 이해하기 쉽게 만듬

<br>
<br>

## CODE

<br>

- Actions

```javascript
const TaskActions = {
    addTask(task) {
        Dispatcher.dispatch({
            actionType: 'ADD_TASK',
            task: task
        });
    },
    removeTask(taskId) {
        Dispatcher.dispatch({
            actionType: 'REMOVE_TASK',
            taskIdd: taskId
        });
    }
}
```

- Dispatcher

```javascript
const Dispatcher = new Flux.Dispatcher();

export default Dispatcher;
```

- Stores

```javascript
class TaskStore extends Flux.Store {
    constructor() {
        super(Dispatcher);

        this.state = {
            tasks: []
        };
    }

    handleDispatch(payload) {
        switch (payload.actionType) {
            case 'ADD_TASK':
                this.state.tasks.push(payload.task);

                this.__emitChange();
                break;
            case 'REMOVE_TASK':
                this.state.tasks = this.state.tasks.filter(task => task.id !== payload.taskId);
                this.__emitChange();
                break;
            default:
        }
    }
}

export default new TaskStore();
```

- View

```javascript
class TaskView extends React.Component {
    constructor(props) {
        super(props);

        this.state = {
            tasks: TaskStore.getState().tasks
        };
    }

    componentDidMount() {
        TaskStore.addListener(() => {
            this.setState({
                tasks: TaskStore.getState().tasks
            });
        });
    }

    render() {
        return (
            <ul>
                {this.state.tasks.map(task => <li key={task.id}>{task.name}</li>)}
            </ul>
        );
    }
}
```

- 설명

```
단방향 데이터 흐름은 애플리케이션의 동작을 
보다 예측 가능하고 이해하기 쉽게 만듬

상태의 변경 사항은 구성 요소를 통해 
아래로 전파되지만 구성 요소는 상태를 
직접 업데이트할 수 없음

대신 상태를 업데이트하는 중앙 저장소에서 
처리하는 작업만 트리거할 수 있음

이러한 관심사의 분리와 중앙 집중식 상태 관리를 통해 
특히 대규모 애플리케이션의 경우 코드를 보다 쉽게 ​​관리
```