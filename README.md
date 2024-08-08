# Codsoft-
task 1
                                                                               
    import json
     class Task:
    def __init__(self, description, completed=False):
        self.description = description
        self.completed = completed

    def __repr__(self):
        status = "✓" if self.completed else "✗"
        return f"[{status}] {self.description}"

    def mark_complete(self):
        self.completed = True

    class ToDoList:
    def __init__(self):
        self.tasks = []
        self.load_tasks()

    def add_task(self, description):
        self.tasks.append(Task(description))
        self.save_tasks()

    def view_tasks(self):
        for i, task in enumerate(self.tasks, 1):
            print(f"{i}. {task}")

    def update_task(self, index, description):
        if 0 <= index < len(self.tasks):
            self.tasks[index].description = description
            self.save_tasks()
        else:
            print("Invalid task number.")

    def delete_task(self, index):
        if 0 <= index < len(self.tasks):
            del self.tasks[index]
            self.save_tasks()
        else:
            print("Invalid task number.")

    def mark_task_complete(self, index):
        if 0 <= index < len(self.tasks):
            self.tasks[index].mark_complete()
            self.save_tasks()
        else:
            print("Invalid task number.")

    def save_tasks(self):
        with open('tasks.json', 'w') as file:
            json.dump([task.__dict__ for task in self.tasks], file)

    def load_tasks(self):
        try:
            with open('tasks.json', 'r') as file:
                tasks_data = json.load(file)
                self.tasks = [Task(**data) for data in tasks_data]
        except FileNotFoundError:
            self.tasks = []

     def main():
    todo_list = ToDoList()
    while True:
        print("\n1. Add Task\n2. View Tasks\n3. Update Task\n4. Delete Task\n5. Mark Task Complete\n6. Exit")
        choice = input("Choose a number: ")
        if choice == '1':
            description = input("Enter task description: ")
            todo_list.add_task(description)
        elif choice == '2':
            todo_list.view_tasks()
        elif choice == '3':
            index = int(input("Enter task number to update: ")) - 1
            description = input("Enter new description: ")
            todo_list.update_task(index, description)
        elif choice == '4':
            index = int(input("Enter task number to delete: ")) - 1
            todo_list.delete_task(index)
        elif choice == '5':
            index = int(input("Enter task number to mark complete: ")) - 1
            todo_list.mark_task_complete(index)
        elif choice == '6':
            break
        else:
            print("Invalid choice. Try again.")

     if __name__ == "__main__":
    main()
task 2
            
    def add(a, b):
    return a + b

    def subtract(a, b):
    return a - b

    def multiply(a, b):
    return a * b

    def divide(a, b):
    if b == 0:
        return "Error: Division by zero is not allowed."
    return a / b

    def main():
    print("Calculator")

    # Input numbers
    try:
        num1 = float(input("Enter the first number: "))
        num2 = float(input("Enter the second number: "))
    except ValueError:
        print("Invalid input. Please enter numeric values.")
        return

    # Input operation choice
    print("\nSelect operation:")
    print("1. add")
    print("2. subtract")
    print("3. multiply")
    print("4. divide")

    operation = input("Enter the operation (1/2/3/4): ")

    if operation == '1':
        result = add(num1, num2)
        op_symbol = '+'
    elif operation == '2':
        result = subtract(num1, num2)
        op_symbol = '-'
    elif operation == '3':
        result = multiply(num1, num2)
        op_symbol = '*'
    elif operation == '4':
        result = divide(num1, num2)
        op_symbol = '/'
    else:
        print("Invalid operation choice.")
        return

    # Display result
    if isinstance(result, str):  # For error messages
        print(result)
    else:
        print(f"{num1} {op_symbol} {num2} = {result}")

    if __name__ == "__main__":
    main()
task 3

    import random
    import string

     def generate_password(length):
    """Generate a random password of the specified length."""
    # Define the characters to use for the password
    characters = string.ascii_letters + string.digits + string.punctuation

    # Generate the password
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

    def main():
    print("Password Generator")

    # Prompt user to specify the length of the password
    while True:
        try:
            length = int(input("Enter the desired length of the password: "))
            if length <= 0:
                print("Password length must be a positive integer.")
            else:
                break
        except ValueError:
            print("Invalid input. Enter a numeric value.")

    # Generate and display the password
    password = generate_password(length)
    print(f"Generate password: {password}")

    if __name__ == "__main__":
    main()


