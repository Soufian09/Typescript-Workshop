## Let's go 

Supprimez le fichier ```App.css``` , ensuite sur votre fichier ```App.tsx``` , coller ce bout de code ci-dessous .

``` import React, { Component } from "react";

class App extends Component {
  render() {
    return (
      <div>
        <h2>Hello React TS!</h2>
      </div>
    );
  }
}

export default App; 
```

Jusqu'à présent, il semble identique à un composant JS React. La prochaine chose que nous pourrions considérer est quelles données notre application conservera-t-elle. Fondamentalement, certaines tâches. Nous allons définir un modèle de tâche dans un dossier séparé, ce qui est une bonne pratique. Dans ``` src/models/task.ts ```

```
export interface Task {
  id: number;
  name: string;
}
```

### Créer une tâche
Créons notre premier composant dans components/NewTaskForm.tsx

```
import React, { FunctionComponent } from "react";
import { Task } from "../models/task";

interface Props {
  onChange: (event: React.ChangeEvent<HTMLInputElement>) => void;
  onAdd: (event: React.FormEvent<HTMLFormElement>) => void;
  task: Task;
}

export const NewTaskForm: FunctionComponent<Props> = ({
  onChange,
  onAdd,
  task
}) => (
  <form onSubmit={onAdd}>
    <input onChange={onChange} value={task.name} />
    <button type="submit">Add a task</button>
  </form>
);
```
### Aller sur votre fichier App.tsx 

- On va devoir inserer ici ce que nous avions coder sur le fichier NewTaskForm pour affichier notre form , pour cela vous allez mettre ceci : 

``` 
interface State {
  newTask: Task;
  tasks: Task[];
}

class App extends Component<{}, State> {
  state = {
    newTask: {
      id: 1,
      name: ""
    },
    tasks: []
  };

  render() {
    return (
      <div>
        <h2>Hello React TS!</h2>
        <NewTaskForm
          task={this.state.newTask}
          onAdd={this.addTask}
          onChange={this.handleTaskChange}
        />
      </div>
    );
  }
}
```

### Rendre les tâches et supprimer
- Pour compléter notre application simple, ajoutons une méthode pour supprimer une tâche.
```
private deleteTask = (taskToDelete: Task) => {
  this.setState(previousState => ({
    tasks: [
      ...previousState.tasks.filter(task => task.id !== taskToDelete.id)
    ]
  }));
};
```

- Ensuite, une liste de tâches avec un élément à l'intérieur:

Dans ```src/components/TaskList.tsx```:

```
import React, { FunctionComponent } from "react";

import { Task } from "../models/task";
import { TaskListItem } from "./TasksListItem";

interface Props {
  tasks: Task[];
  onDelete: (task: Task) => void;
}

export const TasksList: FunctionComponent<Props> = ({ tasks, onDelete }) => (
  <ul>
    {tasks.map(task => (
      <TaskListItem task={task} onDelete={onDelete} />
    ))}
  </ul>
);
```

Dans ```src/components/TaskListItem.tsx```:

```
import React, { FunctionComponent } from "react";

import { Task } from "../models/task";

interface Props {
  task: Task;
  onDelete: (task: Task) => void;
}

export const TaskListItem: FunctionComponent<Props> = ({ task, onDelete }) => {
  const onClick = () => {
    onDelete(task);
  };

  return (
    <li>
      {task.name} <button onClick={onClick}>X</button>
    </li>
  );
};
```

TADAAAA ....