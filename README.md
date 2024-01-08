# Password-Generator

# Importing Libraries

from tkinter import *
import random
import string
import pyperclip

# Initializing window

root =Tk()
root.geometry("400x400")
root.resizable(0,0)
root.title("DataFlair - PASSWORD GENERATOR")

# Tk() initialized tkinter which means window created /n geometry() set the width and height of the window /n resizable(0,0) set the fixed size of the window /n title() set the title of the window.

# Heading

heading = Label(root, text = 'PASSWORD GENERATOR' , font ='arial 16 bold').pack()
Label(root, text ='DataFlair', font ='arial 15 bold').pack(side = BOTTOM)

# root is the name which we refer to our window
# text which we display on the label
# font in which the text is written
# pack organized widget in block

# Select password length

pass_label = Label(root, text = 'PASSWORD LENGTH', font = 'arial 10 bold').pack()
pass_len = IntVar()
length = Spinbox(root, from_ = 8, to_ = 32 , textvariable = pass_len , width = 15).pack()

# pass_len is an integer type variable that stores the length of a password.
# To select the password length we use Spinbox() widget.
# Spinbox() widget is used to select from a fixed number of values. Here the value from 8 to 32.

# Function to Generate Password

pass_str = StringVar()

def Generator():
    password = ''
    for x in range (0,4):
        password = random.choice(string.ascii_uppercase)+random.choice(string.ascii_lowercase)+random.choice(string.digits)+random.choice(string.punctuation)
    for y in range(pass_len.get()- 4):
        password = password+random.choice(string.ascii_uppercase + string.ascii_lowercase + string.digits + string.punctuation)
    pass_str.set(password)

# pass_str is a string type variable that stores the generated password
# password = “” is the empty string
# First loop will generate a string of length 4 which is a combination of an uppercase letter, a lowercase letter, digits, and a special symbol and that string will store in password variable.
# The second loop will generate a random string of length entered by the user – 4 and add to the password variable. Here we minus 4 to the length of the user because we already generate the string of length 4.
W# e have done this because we want a password which must contain an uppercase, a lowercase, a digit, and a special symbol.

# Now the password is set to the pass_str() variable.

Button(root, text = "GENERATE PASSWORD" , command = Generator ).pack(pady= 5)
Entry(root , textvariable = pass_str).pack()

# Button() widget used to display button on our window
# command is called when the button is click
# Entry() widget used to create an input text field
# textvariable used to retrieve the current text to the entry widget

# Function to Copy Password

def Copy_password():
    pyperclip.copy(pass_str.get())

Button(root, text = 'COPY TO CLIPBOARD', command = Copy_password).pack(pady=5)

# pyperclip.copy() used to copy the text to clipboard

# Loop to run program

root.mainloop()

