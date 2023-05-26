# Daily-Activities-App
A simple Todo List
import tkinter as tk

# Create the main window
root = tk.Tk()
root.title("To-Do App")

# Create a frame to hold the list of tasks
tasks_frame = tk.Frame(root)

# Create a listbox to display the tasks
tasks_listbox = tk.Listbox(tasks_frame)

# Create a label to display the current date and time
date_time_label = tk.Label(root, text="Today is: " + str(tk.now()))

# Create a button to add a new task
add_task_button = tk.Button(root, text="Add Task", command=add_task)

# Create a button to mark a task as completed
mark_completed_button = tk.Button(root, text="Mark Completed", command=mark_completed)

# Create a button to clear the list of tasks
clear_list_button = tk.Button(root, text="Clear List", command=clear_list)

# Pack all of the widgets
tasks_frame.pack()
tasks_listbox.pack()
date_time_label.pack()
add_task_button.pack()
mark_completed_button.pack()
clear_list_button.pack()

# Create a list to store the tasks
tasks = []

# Define a function to add a new task
def add_task():
    # Get the task from the user
    task = input("Enter a task: ")

    # Add the task to the list
    tasks.append(task)

    # Update the listbox
    tasks_listbox.insert(tk.END, task)

# Define a function to mark a task as completed
def mark_completed():
    # Get the selected task
    task = tasks_listbox.get(tk.ACTIVE)

    # Remove the task from the list
    tasks.remove(task)

    # Update the listbox
    tasks_listbox.delete(tk.ACTIVE)

    # Add a checkmark to the task
    tasks_listbox.insert(tk.ACTIVE, task + " ✔")

# Define a function to clear the list of tasks
def clear_list():
    # Clear the list of tasks
    tasks.clear()

    # Update the listbox
    tasks_listbox.delete(0, tk.END)

# Start the main loop
root.mainloop()
