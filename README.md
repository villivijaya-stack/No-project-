# No-project-
For student 
calculator-project-for-student
The Calculator Project is a basic application designed to perform simple arithmetic operations like Addition, Subtraction, Multiplication, and Division. The main objective of this project is to help students understand the fundamentals of programming logic, user input handling, and mathematical operations in code. import tkinter as tk

def create_calculator(): root = tk.Tk() root.title("Arulananthu Calculator")

# Entry widget to display input and results
entry = tk.Entry(root, width=30, borderwidth=5)
entry.grid(row=0, column=0, columnspan=4, padx=10, pady=10)

# Function to update the entry widget
def button_click(number):
    current = entry.get()
    entry.delete(0, tk.END)
    entry.insert(0, str(current) + str(number))

# Function for clear button
def button_clear():
    entry.delete(0, tk.END)

# Function for equals button (you'll implement the calculation logic here)
def button_equal():
    try:
        expression = entry.get()
        result = eval(expression) # Be cautious with eval in real apps, but fine for simple calcs
        entry.delete(0, tk.END)
        entry.insert(0, str(result))
    except: 
        entry.delete(0, tk.END)
        entry.insert(0, "Error")

# Define buttons
buttons = [
    ('7', 1, 0), ('8', 1, 1), ('9', 1, 2), ('/', 1, 3),
    ('4', 2, 0), ('5', 2, 1), ('6', 2, 2), ('*', 2, 3),
    ('1', 3, 0), ('2', 3, 1), ('3', 3, 2), ('-', 3, 3),
    ('0', 4, 0), ('.', 4, 1), ('=', 4, 2), ('+', 4, 3)
]

# Create and place buttons
for (text, row, col) in buttons:
    if text == '=':
        btn = tk.Button(root, text=text, padx=20, pady=10, command=button_equal)
    else:
        btn = tk.Button(root, text=text, padx=20, pady=10, command=lambda t=text: button_click(t))
    btn.grid(row=row, column=col)

# Clear button
clear_button = tk.Button(root, text="C", padx=20, pady=10, command=button_clear)
clear_button.grid(row=5, column=0, columnspan=1) # Adjust row and column as needed

root.mainloop()
create_calculator()
