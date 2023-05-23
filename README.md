# todolist
def show_menu():
    print("Menu:")
    print("1. View to-do list")
    print("2. Add task")
    print("3. Mark task as complete")
    print("4. Remove task")
    print("5. Exit")

def view_todo_list(todo_list):
    if not todo_list:
        print("Your to-do list is empty.")
    else:
        print("To-Do List:")
        for index, task in enumerate(todo_list, start=1):
            print(f"{index}. {task}")

def add_task(todo_list):
    task = input("Enter the task to add: ")
    todo_list.append(task)
    print("Task added successfully.")

def mark_complete(todo_list):
    view_todo_list(todo_list)
    if not todo_list:
        return

    task_index = int(input("Enter the index of the task to mark as complete: ")) - 1

    if task_index < 0 or task_index >= len(todo_list):
        print("Invalid task index.")
    else:
        todo_list[task_index] += " [COMPLETE]"
        print("Task marked as complete.")

def remove_task(todo_list):
    view_todo_list(todo_list)
    if not todo_list:
        return

    task_index = int(input("Enter the index of the task to remove: ")) - 1

    if task_index < 0 or task_index >= len(todo_list):
        print("Invalid task index.")
    else:
        removed_task = todo_list.pop(task_index)
        print(f"Task '{removed_task}' removed successfully.")

def todo_list_manager():
    todo_list = []

    while True:
        show_menu()
        choice = input("Enter your choice (1-5): ")

        if choice == "1":
            view_todo_list(todo_list)
        elif choice == "2":
            add_task(todo_list)
        elif choice == "3":
            mark_complete(todo_list)
        elif choice == "4":
            remove_task(todo_list)
        elif choice == "5":
            print("Exiting the program...")
            break
        else:
            print("Invalid choice. Please try again.")

todo_list_manager()
