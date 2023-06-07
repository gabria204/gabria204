port mysql.connector as mycon
conn=mycon.connect(host="localhost",user="root",passwd="root")
cur=conn.cursor()
cur.execute("create database if not exists 5starhotel")
cur.execute("use 5starhotel")
from tkinter import *
from tkinter import messagebox as msg
#TO choose details
def addemp():
    m=Tk()
    m.geometry('2000x2000')
    m.title('details')
    m['bg']='cyan'
    l=Label(m,text='staff details',font=('cosmic san ms',17))
    l.place(x=100,y=50)
##    l1=Button(m,text='addemp',font=29) 
##    l1.place(x=100,y=100)
    e=Label(m,text="Enter emp no",font=("cosmic san ms",17))
    e.place(x=100,y=150)
    e1=Entry(m)
    e1.place(x=600,y=150)
    n=Label(m,text="\tEnter emp name:",font=("cosmic san ms",17))
    n.place(x=100,y=200)
    e2=Entry(m)
    e2.place(x=600,y=200)
    doj=Label(m,text="\tEnter date-of-joining(yyyy-mm-dd:",font=("cosmic san ms",17))
    doj.place(x=100,y=250)
    e3=Entry(m)
    e3.place(x=600,y=250)
    dept=Label(m,text="\tEnter department:",font=("cosmic san ms",17))
    dept.place(x=100,y=300)
    e4=Entry(m)
    e4.place(x=600,y=300)
    desig=Label(m,text="\tEnter designation:",font=("cosmic san ms",17))
    desig.place(x=100,y=350)
    e5=Entry(m)
    e5.place(x=600,y=350)
    sal=Label(m,text="\tEnter salary:",font=("cosmic san ms",17))
    sal.place(x=100,y=400)
    e6=Entry(m)
    e6.place(x=600,y=400)
    l6=Button(m,text="saveemp",font=("cosmic san ms",17))
    l6.place(x=600,y=460)
    sq="insert into staffdetails values('{}','{}','{}','{}','{}','{}')".format(e,n,doj,dept,desig,sal)
    
    cur.execute(sq)
    conn.commit()
    print("employee data inserted successfully")
##    l6=Button(m,text="saveemp",font=100,command=NextPage)
##    l6.place(x=600,y=460)
    def displayAll():
        mycursor=mycon.execute("select*from staffdetails limit 0,10")
        i=0
        for t in mycursor:
            for d in range(len(t)):
                e=Label(m,width=8,fg="blue",text=t[d],relief="ridge",anchor="w")
                e.grid(row=i,column=d)
        i=i+1
    display()
    m.mainloop()
def update():
    m=Tk()
    m.geometry('2000x2000')
    m.title('update')
    m['bg']='purple'
    y=Label(m,text="\t1.Department",font=("cosmic san ms",25))
    y.place(x=100,y=200)
    z=Label(m,text="\t2.designation",font=("cosmic san ms",25))
    z.place(x=100,y=250)
    x=Label(m,text="\t3.salary",font=("cosmic san ms",25))
    x.place(x=100,y=300)
    l2=Button(m,text="enter your choice:",font=("cosmic san ms",25))
    l2.place(x=100,y=100)
    e8=Entry(m)
    e8.place(x=500,y=100)
    e3=Button(m,text='Enter',font=("cosmic san ms",25),command=enter)
    e3.place(x=500,y=410)
    e4=Button(m,text='Clear',font=("cosmic san ms",25))
    e4.place(x=450,y=500)
    e5=Button(m,text='Back',font=("cosmic san ms",25),command=m.destroy)
    e5.place(x=450,y=600)
def enter():
    m=Tk()
    m.geometry('1000x1000')
    m.title("update")
    m['bg']='cyan'
##    if e3=="department":
    l=Label(m,text="enter new department:",font=("cosmic san ms",25))
    l.place(x=0,y=100)
    l1=Entry(m)
    l1.place(x=100,y=150)
##        sq="update employee set{}='{}' where emp no='{}'".format("dept",d,e)
##    elif e3=="designation":
    d=Label(m,text="enter new designation:",font=("cosmic san ms",25))
    d.place(x=0,y=200)
    l2=Entry(m)
    l2.place(x=200,y=250)
##            sq="update employee set{}='{}' where emp no='{}'".format("desig",d,e)
##    elif e3=="salary":
    s=Label(m,text="enter new salary:",font=("cosmic san ms",25))
    s.place(x=0,y=300)
    l3=Entry(m)
    l3.place(x=300,y=300)
    l4=Button(m,text='Enter',font=("cosmic san ms",25),command=showdetails)
    l4.place(x=500,y=410)
##            sq="update employee set{}='{}' where emp no='{}'".format("salary",s,e)
##    else:
##        print("enter valid choice!:")
def showdetails():
    cur.execute("select*from staffdetails")
    
    
                                                            
    
def details():
    def destroy():
        o.destroy
        
    o=Tk()
    o.geometry('1000x1000')
    o.title('CHOOSE YOUR OPTION')
    o['bg']='cyan'
    l=Label(o,text='staff details :',font=('cosmic san ms',25))
    l.place(x=50,y=100)
    l1=Button(o,text='addemp',font=100,command=addemp)
    l1.place(x=150,y=200)
    l2=Button(o,text='updateemp',font=100,command=update)
    l2.place(x=250,y=200)
    l3=Button(o,text='deleteemp',font=100,command=o.destroy)
    l3.place(x=350,y=300)
    bc=Button(o,text='Back',font=100,command=o.destroy)
    bc.place(x=750,y=500)
def snack():
    a=Tk()
    a.geometry("100x100")
    a["bg"]="pink"
    s=Label(a,text="SNACKS TIME!!!\n5 star hotel",font=("cosmic san ms",25))
    s.place(x=120,y=250)
    s1=Button(a,text="NOODLES\t\t\t\t\t\t\t\tCONTINENTAL DISHES",font=("cosmic san ms",25))
    s1.place(x=140,y=250)
    s2=Button(a,text="tomato shorba=Rs.125\t\t\t\t\t\t\t\t\t\t\t\t\tplain steak=Rs.70",font=("cosmic san ms",25))
    s2.place(x=160,y=250)
#TO choose the menucard
def menucard():
    a=Tk()
    a.geometry('1000x1000')
    a['bg']='blue'
    t=Label(a,text='food time!!!\nmenu card\n5 star hotel:',font=('cosmic san ms',25))
    t.place(x=100,y=100)
    t1=Button(a,text='snacks',font=100,command=snack)                                      
    t1.place(x=150,y=200)
    t2=Button(a,text='SRK Miraj cinemas',font=100,command=amovie)
    t2.place(x=250,y=300)
    t3=Button(a,text='INOX',font=100,command=amovie)
    t3.place(x=350,y=400)
    t4=Button(a,text='Cinepolis',font=100,command=amovie)
    t4.place(x=450,y=400)
    t5=Button(a,text='Cosmo Cinemas RGB Laser ',font=100,command=amovie)
    t5.place(x=550,y=400)
    t6=Button(a,text=' Baba Cinemas',font=100,command=amovie)
    t6.place(x=650,y=500)
    
    t7=Button(a,text='back',font=100,command=a.destroy)
    t7.place(x=600,y=600)
#reservation
def seat():
    def mb():
        msg.showinfo(message='Enjoy  your show at '+str(e2.get()))
    def clear():
        e2.delete(0,'end')
    w=Tk()
    w.geometry('1000x1000')
    w['bg']='pink'
    p1=Label(w,text='Choose show timings:',font=('cosmic san ms',20))
    p1.place(x=100,y=100)
    p2=Label(w,text='Time slots are:',font=('cosmic san ms',20))
    p2.place(x=100,y=150)
    p3=Label(w,text='screen 1: 10.00-1.00 ; 1.10-4.10 ; 4.20-7.20 ; 7.30-10.30',font=('cosmic san ms',20))
    p3.place(x=100,y=200)
    p4=Label(w,text='screen 2: 10.15-1.15 ; 1.25-4.25 ; 4.35-7.35 ; 7.45-10.45',font=('cosmic san ms',20))
    p4.place(x=100,y=250)
    p5=Label(w,text='screen 3: 10.30-1.30 ; 1.40-4.40 ; 4.50-7.50 ; 8.00-11.00',font=('cosmic san ms',20))
    p5.place(x=100,y=300)
    e1=Label(w,text='Enter screen timing ',font=('cosmic san ms',20))
    e1.place(x=100,y=400)
    e2=Entry(w)
    e2.place(x=400,y=410)
    e3=Button(w,text='Enter',font=100,command=mb)
    e3.place(x=500,y=410)
    e4=Button(w,text='Clear',font=100,command=clear)
    e4.place(x=450,y=500)
    e5=Button(w,text='Back',font=100,command=w.destroy)
    e5.place(x=450,y=600)
###Driver code
k=Tk()
k.geometry('750x750')
k.title('HOTEL MANAGEMENT')
k['bg']='magenta'
c=Label(k,text='HOTEL MANAGEMENT',font=('bradley hand itc',25))
c.place(x=100,y=50)
c1=Label(k,text='Please Enter Your Choice',font=('bradley hand itc',25))
c1.place(x=100,y=150)
c2=Button(k,text='staff details',font=100,command=details)
c2.place(x=150,y=300)
c3=Button(k,text='menucard',font=100,command=menucard)
c3.place(x=250,y=400)
c4=Button(k,text='reservation',font=100,command=seat)
c4.place(x=350,y=300)
c5=Button(k,text='Exit',font=100,command=k.destroy)
c5.place(x=250,y=500)

