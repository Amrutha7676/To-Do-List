# To-Do-List
class ToDoList:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append({'task': task, 'done': False})

    def remove_task(self, task_id):
        try:
            del self.tasks[task_id]
        except IndexError:
            print("Task not found!")

    def mark_done(self, task_id):
        try:
            self.tasks[task_id]['done'] = True
        except IndexError:
            print("Task not found!")

    def show_tasks(self):
        if not self.tasks:
            print("No tasks to show.")
        else:
            for idx, task in enumerate(self.tasks):
                status = "Done" if task['done'] else "Not done"
                print(f"{idx + 1}. {task['task']} - {status}")


def main():
    todo_list = ToDoList()
    while True:
        print("\nTo-Do List Menu:")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Remove Task")
        print("4. Mark Task as Done")
        print("5. Exit")

        choice = input("Choose an option: ")

        if choice == '1':
            task = input("Enter the task: ")
            todo_list.add_task(task)

        elif choice == '2':
            todo_list.show_tasks()

        elif choice == '3':
            todo_list.show_tasks()
            task_id = int(input("Enter the task number to remove: ")) - 1
            todo_list.remove_task(task_id)

        elif choice == '4':
            todo_list.show_tasks()
            task_id = int(input("Enter the task number to mark as done: ")) - 1
            todo_list.mark_done(task_id)

        elif choice == '5':
            print("Exiting To-Do List Application. Goodbye!")
            break

        else:
            print("Invalid choice! Please choose a valid option.")


if __name__ == "__main__":
    main()
