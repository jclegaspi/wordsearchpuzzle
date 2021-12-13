# wordsearchpuzzle
import tkinter
from tkinter import *
import random
from tkinter import messagebox

root = tkinter.Tk()

answers=["apple","mango","banana",'achieve','kolkata','evening','servant','receiver','london','ferrari','hollow','horror','master','morning','bottle','pen','router','copy','narrow','wide','dive','love','block','right','simple','deaf','single','knight','hope']
words=['plpea','gnoma','annaba','hveeica','lkaatko','egvnine','aestnrv','iceever','lndono','rrreifa','wllhoo','oohrrr','rtemsa','nnrgimo','lttobe','enp','ourrte','ypco','rraonw','wdie','ievd','elov','klboc','ightr','plmsie','dfea','glneis','ghtkni','opeh']

num=random.randrange(0,len(words),1)
c=0
d=0
s = ""
l = Label(root)

def reset():
    global words, answers, num
    num=random.randrange(0,len(words),1)
    label.config(text = words[num])
    e1.delete(0, END)

def default():
    global words,answers,num
    label.config(text = words[num])

def checkans():
    global words, answers, num, c, d, s, l
    d=int(d)+1
    var = e1.get() 
    if var == answers[num]:
        messagebox.showinfo("Congratulations", "It's the correct answer!!")
        c = int(c)+1
    else:
        messagebox.showerror("Sorry", "It's not the correct answer.")
    s = 'Score :' + str(c) + '/' + str(d)
    l.forget()
    l = Label(root, font=("Verdana", 20), text=s, bg="#000000", fg="#fff", )
    l.pack(side=LEFT)
    reset()


root.geometry("500x500+500+150")
root.title("Jumbled word game")
root.configure(background="#000000")

Label(root,text="JUMBLED WORD GAME",font = ("Verdana",28),bg = "#000000", fg = "#fff").pack(pady = 5)
label = Label(root,font = ("Verdana",22),bg = "#000000", fg = "#fff")
label.pack(pady = 30,ipady=10,ipadx=10)

ans = StringVar()
e1 = Entry(root,font = ("Verdana",20),textvariable = ans,)
e1.pack(ipady=5,ipadx=5) 
Button(root,text = "Check",font = ("Comic sans ms",20),width = 10,bg="#333945",fg="#45CE30",relief = GROOVE,command = checkans,).pack(pady = 40) 
Button(root,text = "Reset",font = ("Comic sans ms",20),width = 10,bg="#777E8B",fg="#E1DA00",relief = GROOVE,command = reset).pack() 

default()

root.mainloop()
