class ToDoList:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append({"task": task, "done": False})
        print(f"Added task: {task}")

    def remove_task(self, task):
        for t in self.tasks:
            if t["task"] == task:
                self.tasks.remove(t)
                print(f"Removed task: {task}")
                return
        print(f"Task '{task}' not found.")

    def view_tasks(self):
        if not self.tasks:
            print("No tasks in your To-Do list.")
            return
        for idx, task in enumerate(self.tasks, 1):
            status = "Done" if task["done"] else "Not Done"
            print(f"{idx}. {task['task']} - {status}")

    def mark_done(self, task):
        for t in self.tasks:
            if t["task"] == task:
                t["done"] = True
                print(f"Marked '{task}' as done.")
                return
        print(f"Task '{task}' not found.")

def main():
    todo_list = ToDoList()

    while True:
        print("\nTo-Do List Menu:")
        print("1. Add Task")
        print("2. Remove Task")
        print("3. View Tasks")
        print("4. Mark Task as Done")
        print("5. Exit")
        
        choice = input("Choose an option (1-5): ")
        
        if choice == '1':
            task = input("Enter the task to add: ")
            todo_list.add_task(task)
        elif choice == '2':
            task = input("Enter the task to remove: ")
            todo_list.remove_task(task)
        elif choice == '3':
            todo_list.view_tasks()
        elif choice == '4':
            task = input("Enter the task to mark as done: ")
            todo_list.mark_done(task)
        elif choice == '5':
            print("Goodbye!")
            break
        else:
            print("Invalid choice, please try again.")

if __name__ == "__main__":
    main()
