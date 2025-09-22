# To-Do-list
tasks = []  # Global list to store tasks
def show_tasks():
    """Display all tasks"""
    if not tasks:
        print("\n✅ No tasks found!\n")
    else:
        print("\n📝 To-Do List:")
        for i, task in enumerate(tasks, start=1):
            status = "✔️ Done" if task["done"] else "❌ Not Done"
            print(f"{i}. {task['title']} [{status}]")
        print()


def add_task():
    """Add a new task"""
    title = input("Enter task title: ").strip()
    if title:
        tasks.append({"title": title, "done": False})
        print("✅ Task added successfully!\n")
    else:
        print("⚠️ Task title cannot be empty!\n")


def update_task():
    """Update an existing task"""
    show_tasks()
    if not tasks:
        return
    try:
        task_num = int(input("Enter task number to update: "))
        if 1 <= task_num <= len(tasks):
            new_title = input("Enter new task title: ").strip()
            if new_title:
                tasks[task_num - 1]["title"] = new_title
                print("✅ Task updated successfully!\n")
            else:
                print("⚠️ Task title cannot be empty!\n")
        else:
            print("⚠️ Invalid task number!\n")
    except ValueError:
        print("⚠️ Please enter a valid number!\n")


def mark_done():
    """Mark task as completed"""
    show_tasks()
    if not tasks:
        return
    try:
        task_num = int(input("Enter task number to mark as done: "))
        if 1 <= task_num <= len(tasks):
            tasks[task_num - 1]["done"] = True
            print("✅ Task marked as done!\n")
        else:
            print("⚠️ Invalid task number!\n")
    except ValueError:
        print("⚠️ Please enter a valid number!\n")


def delete_task():
    """Delete a task"""
    show_tasks()
    if not tasks:
        return
    try:
        task_num = int(input("Enter task number to delete: "))
        if 1 <= task_num <= len(tasks):
            removed = tasks.pop(task_num - 1)
            print(f"🗑️ Task '{removed['title']}' deleted successfully!\n")
        else:
            print("⚠️ Invalid task number!\n")
    except ValueError:
        print("⚠️ Please enter a valid number!\n")


def main():
    """Main menu"""
    while True:
        print("==== To-Do List App ====")
        print("1. Show Tasks")
        print("2. Add Task")
        print("3. Update Task")
        print("4. Mark Task as Done")
        print("5. Delete Task")
        print("6. Exit")

        choice = input("Enter choice (1-6): ")

        if choice == "1":
            show_tasks()
        elif choice == "2":
            add_task()
        elif choice == "3":
            update_task()
        elif choice == "4":
            mark_done()
        elif choice == "5":
            delete_task()
        elif choice == "6":
            print("👋 Exiting... Goodbye!")
            break
        else:
            print("⚠️ Invalid choice! Please try again.\n")


if __name__ == "__main__":
    main()
