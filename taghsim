from tkinter import *

root = Tk()
root.minsize(600,400)
root.maxsize(600,400)
root.configure(bg='#189AB4')
root.title('music_collection')
Label(root, text="A:", font=("", 16), bg='#189AB4').place(x=20, y=10)
A = Entry(root, font=("", 16))
A.place(x=70, y=10)
Label(root, text="B:", font=("", 16), bg='#189AB4').place(x=20, y=50)
B = Entry(root, font=("", 16))
B.place(x=70, y=50)
labels = []

def start():
    global var, skip, labels, line
    #pak kardan 
    kg.configure(text="")
    la.configure(text="")
    lb.configure(text="")
    El.configure(text="")
    Bl.configure(text="")
    scl.configure(text="")
    Cl.configure(text="")
    for i in labels: 
        i.destroy()
    canvas.delete(line)

    btn_start.place(x=1000, y=1000)
    button.place(x=70, y=100)

    A.configure(state="disable")
    B.configure(state="disable")
    
    def add(x, y):   #jame adad bar mabnaye 2
        sum = bin(int(x, 2) + int(y, 2))
        sum = sum[2:]
        if len(x) < len(sum):        
            return sum[1:], "1"
        elif len(x) > len(sum):
            for i in range(len(x)-len(sum)):
                sum = "0" + sum
            return sum, "0"
        else:
            return sum, "0"

    def invert(x):   #manfi kardan adad
        t = ""
        x = x[:-count]
        for i in range(len(x)):
            if x[i] == "0":
                t = t + "1"
            else:
                t = t + "0"
        t=add(t, "00000001")[0]
        for i in range(0,count):
            t = t + "0"
        return t

    def shift(x):   #shift be rast
        e = x[0]
        x = x[1:] + "0"
        return x,e


    a = A.get()
    b = B.get()
    sc = len(b)
    count=0
    
    la.configure(text=a, font=("", 13), width=16, anchor="e")
    lb.config(text=b, font=("", 12), width=8, anchor="e")

    button.wait_variable(var)  #entezar
    if not skip:
        var.set(0)

    for i in range(len(b), len(a)):
        b = b + "0"
        count+=1

    #baresi ghabele anjam bodan taghsim
   
    javab = ""
    err = True
    try:
        p, e = add(a, invert(b))
    except:
        javab = "Error"
        kg.configure(text=javab, font=("", 12))
        err = False

    if err:
        if e == "1":
            javab = "!تقسیم نمی شود"
            kg.configure(text=javab, font=("", 12))
            err = False

    px , py = 20, 55
    if err:
        Bl.configure(text=invert(b)[:-count])
        scl.configure(text=sc)
    
    
    while(sc!=0 and err):
        a, e = shift(a)
        El.configure(text=e)
        tmp = Label(root, text="shift", font=("", 13), bg="#189AB4" )
        tmp.place(x=330, y=py+10)
        labels.append(tmp)

        tmp = Label(canvas, text=a[:-count], font=("", 13), bg="#189AB4", width=16, anchor="e" )
        tmp.place(x=px, y=py)
        labels.append(tmp)
        py += 20
        button.wait_variable(var)
        if not skip:
            var.set(0)
        if e == "1":
            javab =  javab + "1" 
            kg.configure(text=javab)
            button.wait_variable(var)
            if not skip:
                var.set(0)

            a, e = add(a, invert(b))
            El.configure(text=e)
            tmp = Label(root, text="sub", font=("", 13), bg="#189AB4" )
            tmp.place(x=330, y=py+10)
            labels.append(tmp)
            tmp = Label(canvas, text=a[:-count], font=("", 13), bg="#189AB4", width=16, anchor="e" )
            tmp.place(x=px, y=py)
            labels.append(tmp)
            py += 20
            sc -=1
            scl.configure(text=sc)
            button.wait_variable(var)
            if not skip:
                var.set(0)
        else:
            a, e = add(a, invert(b))
            El.configure(text=e)
            tmp = Label(root, text="sub", font=("", 13), bg="#189AB4" )
            tmp.place(x=330, y=py+10)
            labels.append(tmp)
            tmp = Label(canvas, text=a[:-count], font=("", 13), bg="#189AB4", width=16, anchor="e" )
            tmp.place(x=px, y=py)
            labels.append(tmp)
            py += 20
            button.wait_variable(var)
            if not skip:
                var.set(0)
            if e == "1":
                javab =  javab + "1" 
                kg.configure(text=javab)
                sc -=1
                scl.configure(text=sc)
                button.wait_variable(var)
                if not skip:
                    var.set(0)
            else:
                javab =  javab + "0" 
                kg.configure(text=javab)
                sc-=1 
                scl.configure(text=sc)
                button.wait_variable(var)
                if not skip:
                    var.set(0)
                while(sc!=0):
                    a, e = shift(a)
                    El.configure(text=e)
                    tmp = Label(root, text="shift", font=("", 13), bg="#189AB4" )
                    tmp.place(x=330, y=py+10)
                    labels.append(tmp)
                    tmp = Label(canvas, text=a[:-count], font=("", 13), bg="#189AB4", width=16, anchor="e" )
                    tmp.place(x=px, y=py)
                    labels.append(tmp)
                    py += 20
                    button.wait_variable(var)
                    if not skip:
                        var.set(0)
                    a, e = add(e + a, "0" + b)
                    El.configure(text=a[0])
                    a = a[1:]
                    tmp = Label(root, text="add AE", font=("", 13), bg="#189AB4" )
                    tmp.place(x=330, y=py+10)
                    labels.append(tmp)
                    Cl.configure(text=e)
                    tmp = Label(canvas, text=a[:-count], font=("", 13), bg="#189AB4", width=16, anchor="e" )
                    tmp.place(x=px, y=py)
                    labels.append(tmp)
                    py += 20
                    button.wait_variable(var)
                    if not skip:
                        var.set(0)
                    if e == "1":
                        javab =  javab + "1" 
                        kg.configure(text=javab)
                        sc -=1
                        scl.configure(text=sc)
                        button.wait_variable(var)
                        if not skip:
                            var.set(0)
                        break
                    else:
                        javab =  javab + "0" 
                        kg.configure(text=javab)
                        sc -=1
                        scl.configure(text=sc)
                        button.wait_variable(var)
                        if not skip:
                            var.set(0)
                        if sc==0:
                            a, e = add(a, b)
                            El.configure(text=e)
                            tmp = Label(root, text="add", font=("", 13), bg="#189AB4" )
                            tmp.place(x=330, y=py+10)
                            labels.append(tmp)
                            tmp = Label(canvas, text=a[:-count], font=("", 13), bg="#189AB4", width=16, anchor="e" )
                            tmp.place(x=px, y=py)
                            labels.append(tmp)
                            py += 20
                            button.wait_variable(var)
                            if not skip:
                                var.set(0)
    if err:
        line = canvas.create_line(0, py+10, 180, py+10, fill='black', width=2)
        py += 12
        tmp = Label(canvas, text=a[:-count], font=("", 13), bg="#189AB4", width=16, anchor="e" )
        tmp.place(x=px, y=py)
        labels.append(tmp)
    btn_start.place(x=70, y=100)
    button.place(x=1000, y=1000)
    A.configure(state="normal")
    B.configure(state="normal")
    

canvas = Canvas(root, width=270, height=370, bg='#189AB4')
canvas.place(x=320, y=10)
la = Label(canvas, text="A", font=("", 16), bg="#189AB4")
la.place(x=20, y=18)
lb = Label(canvas, text="B", font=("", 16), bg="#189AB4")
lb.place(x=185, y=18)
canvas.create_line(180, 20, 180, 300, fill='black', width=2)
canvas.create_line(0, 50, 240, 50, fill='black', width=2)
line = canvas.create_line(0, 0, 0, 0)

Label(root, text="E =", font=("", 16), bg="#189AB4").place(x=10, y=200)
El = Label(root, text="", font=("", 16), bg="#189AB4")
El.place(x=45, y=200)

Label(root, text="!B =", font=("", 16), bg="#189AB4").place(x=5, y=240)
Bl = Label(root, text="", font=("", 16), bg="#189AB4")
Bl.place(x=45, y=240)

Label(root, text="sc =", font=("", 16), bg="#189AB4").place(x=5, y=280)
scl = Label(root, text="", font=("", 16), bg="#189AB4")
scl.place(x=45, y=280)

Label(root, text="C =", font=("", 16), bg="#189AB4").place(x=5, y=320)
Cl = Label(root, text="", font=("", 16), bg="#189AB4")
Cl.place(x=45, y=320)

kg = Label(canvas, text="", font=("", 15), bg="#189AB4")
kg.place(x=185, y=55)

var = IntVar()
button = Button(root, text="Continue", bg='#189AB4', width=7, command=lambda: var.set(1), font=("", 16))

skip = False
btn_start = Button(root, text="Start", bg='#189AB4', width=7, font=("", 16), command=start)
btn_start.place(x=70, y=100)
def erfan():
    made_by.configure(text="@gamerfan82")
    made_by.after(3000, lambda:made_by.configure(text="Erfan Sadeghi"))

made_by = Button(root, text="Erfan Sadeghi", font=("", 12), bg="#189AB4", width=12, command=erfan)
made_by.place(x=90, y=370)



root.mainloop()
