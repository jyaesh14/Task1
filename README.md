class TaskManager:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append({"task": task, "completed": False})
        print(f"Task '{task}' added successfully.")

    def complete_task(self, task_index):
        if 0 <= task_index < len(self.tasks):
            self.tasks[task_index]["completed"] = True
            print(f"Task '{self.tasks[task_index]['task']}' marked as completed.")
        else:
            print("Invalid task index. Please try again.")

    def remove_task(self, task_index):
        if 0 <= task_index < len(self.tasks):
            removed_task = self.tasks.pop(task_index)
            print(f"Task '{removed_task['task']}' removed successfully.")
        else:
            print("Invalid task index. Please try again.")

    def display_tasks(self):
        if not self.tasks:
            print("No tasks available.")
        else:
            print("Tasks:")
            for index, task in enumerate(self.tasks):
                status = "Completed" if task["completed"] else "Incomplete"
                print(f"{index + 1}. {task['task']} - {status}")


def main():
    task_manager = TaskManager()

    while True:
        print("\nTask Manager Menu:")
        print("1. Add Task")
        print("2. Complete Task")
        print("3. Remove Task")
        print("4. Display Tasks")
        print("5. Exit")

        choice = input("Enter your choice (1-5): ")

        if choice == "1":
            task = input("Enter the task: ")
            task_manager.add_task(task)
        elif choice == "2":
            task_manager.display_tasks()
            task_index = int(input("Enter the index of the task to mark as completed: ")) - 1
            task_manager.complete_task(task_index)
        elif choice == "3":
            task_manager.display_tasks()
            task_index = int(input("Enter the index of the task to remove: ")) - 1
            task_manager.remove_task(task_index)
        elif choice == "4":
            task_manager.display_tasks()
        elif choice == "5":
            print("Exiting Task Manager. Goodbye!")
            break
        else:
            print("Invalid choice. Please enter a number between 1 and 5.")


if __name__ == "__main__":
    main()
