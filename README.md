# PythonCalculator
# Built a Calculator using Python script, with Tkinter Toolkit

import tkinter as tk
def press(num):
    global expression
    expression= expression + str(num)
    equation.set(expression)

def equalpress():
    try:
        global expression
        total= str(eval(expression))
        equation.set(total)
        expression= ""
    except:
        equation.set('error')
        expression= ""

def clear():
    global expression
    expression = ""
    equation.set("")

gui= tk.Tk()
gui.configure(background="white")
gui.title("Calculator using Python")
gui.geometry("400x500")
expression=""
equation=tk.StringVar()

expression_field = tk.Entry(gui, textvariable=equation, font=('Calibri',25), bd=9)
expression_field.grid(columnspan=4 , ipadx=10, ipady=10)

button=[
    ('7',1,0),('8',1,1),('9',1,2),('+',1,3),
    ('4',2,0),('5',2,1),('6',2,2),('-',2,3),
    ('1',3,0),('2',3,1),('1',3,2),('*',3,3),
    ('0',4,1),('=',4,2),('/',4,3)
]


for (text,row,col) in button:
    if text== '=':
         action= equalpress
    else:
        action= lambda x=text: press(x)
    tk.Button(gui, text=text, fg="white", bg="black", command=action, height=4, width=9).grid(row=row, column=col)  

tk.Button(gui, text= 'C',fg='black', bg='red', command=clear, height=4, width=9).grid(row=4, column=0)



gui.mainloop()
