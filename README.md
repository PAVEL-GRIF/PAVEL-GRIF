from tkinter import *
import random
import string

root = Tk()
root.resizable(width=False, height=False)
root.title("Генератор паролей by ERMA4")
root.geometry("340x600+300+300")
calculated_text = Text(root, height=30, width=20)

def erase():
    calculated_text.delete('1.0', END)


alfavit = '+-/*ÂÃÄÅÆÇÈÉÊËÌÍÎÏÐÑÒÓÔÕÖØÙÚÛÜÝÞßàáâãäåæçèéêëìíîïðñòóôõö÷øùúûüýþÿ!&)({}[]"\><$#?=@<>abcdefghijklnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890₩ẃẂẁẀẅώℯ£Ē℮ēĖėĘě'

def password():
    for n in range(int(number_entry.get())):
        password = ' '
        for i in range(int(length_entry.get())):
            password += random.choice(alfavit)
        calculated_text.insert(END, password + "\n")


display_button = Button(text="КРУЧУ-ВЕРЧУ", command=password)
erase_button = Button(text="ДАВАЙ ПО-НО-ВО-Й!", command=erase)

number_entry = Entry(width=10, justify=CENTER)
length_entry = Entry(width=10, justify=CENTER)
number_entry.insert(0, "")
length_entry.insert(0, "")

number_label = Label(text="Количество паролей ")
length_label = Label(text="Длина пароля")
number_label.grid(row=0, column=0, sticky="w")
length_label.grid(row=1, column=0, sticky="w")
number_entry.grid(row=0, column=1, padx=1, pady=3)
length_entry.grid(row=1, column=1, padx=1, pady=3)

display_button.grid(row=2, column=0, padx=5, pady=5, sticky="e")
erase_button.grid(row=2, column=2, padx=15, pady=5, sticky="w")
calculated_text.grid(row=4, column=0, sticky='nsew', columnspan=3)

scrollb = Scrollbar(root, command=calculated_text.yview)
scrollb.grid(row=4, column=4, sticky='nsew')
calculated_text.configure(yscrollcommand=scrollb.set)

root.mainloop()
