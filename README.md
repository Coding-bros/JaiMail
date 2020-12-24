# What is this JaiMail?
**JaiMail is a small code representing gmail, it is easy to use and a fun way to send mails to others.**

## What all we need for this to run
### (if the code doesn't work, install all these in a venv)
- Tkinter

it is a default module in python

- Python
    
    brew install python3

#
## code

```python
from tkinter import *
from tkinter.scrolledtext import ScrolledText
import smtplib
import os
import cv2

def btn_clicked():
    get_1 = sender_box.get()
    store_get_1 = get_1

    get_2 = password.get()
    store_get_2 = get_2

    get_3 = reciver_box.get()
    store_get_3 = get_3

    get_4 = mess_box.get()
    store_get_4 = get_4

    try:
        server = smtplib.SMTP('smtp.gmail.com', 587)
        server.ehlo()
        server.starttls()
        server.login(store_get_1, store_get_2)
        server.sendmail(store_get_1, store_get_3, store_get_4)
        statement1 = 'Mail has Been Sent, Thanks For Using JaiMail'
    except:
        statement2 = 'Something Went Wrong.Please Try Agian'
        return statement2

def display_mess():
    display['text'] = btn_clicked()

window = Tk()
window.title('JaiMail')
window.geometry('500x400')
window.config(bg='red')

sender = Label(text="Sender Email", bg="blue")
sender.place(relx = 0.023, rely=0.1)

sender_box = Entry(font=20)
sender_box.place(relx = 0.3, rely=0.1, relwidth = 0.6)

sender_password = Label(text="Password", bg="blue")
sender_password.place(relx=0.023, rely=0.25)

password = Entry(font=20)
password.place(relx=0.3, rely=0.25, relwidth = 0.6)

reciver = Label(text="Recipient Email", bg="blue")
reciver.place(relx=0.023, rely=0.4)
message_label = Label(text="Message Box", bg="orange")
message_label.place(relx=0.4, rely = 0.5)

mess_box = Entry(justify='left')
mess_box.place(relx=0.023, rely = 0.58, relwidth = 0.95, relheight=0.3)

button_send = Button(text="Send", bg="green", fg="white", command=lambda:display_mess(btn_clicked()))
button_send.place(relx = 0.85, rely = 0.9)

display = Label(bg = "slate blue", fg="white", font="bold")
display.place(relx=0.023, rely = 0.9, relheight = 0.07, relwidth = 0.8)

window.mainloop()```
