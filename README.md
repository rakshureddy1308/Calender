from tkinter import *
import calendar

def display_calendar():
    actual_year = int(year_entry.get())

    new_root = Toplevel()
    new_root.title('Calendar Screen')
    new_root.config(bg='black')

    calendar_content = calendar.calendar(actual_year)
    calendar_text = Text(new_root, bg='black', fg='white', font='Consolas 10 bold', height=36, width=100)
    calendar_text.insert(END, calendar_content)
    calendar_text.config(state=DISABLED)
    calendar_text.pack(padx=30, pady=30)

    new_root.mainloop()


def clear_entries():
    year_entry.delete(0, END)


root = Tk()
root.config(bg='black')
root.title('Calendar App')
root.geometry("400x400")

header = Label(root, text='CALENDAR', bg='black', fg='white', font=('Arial', 32, 'bold'))
header.pack(pady=25)

year_frame = Frame(root, bg='black')
year_frame.pack()

lbl = Label(year_frame, text='Enter the year:', bg='black', fg='white', font=('Arial', 14))
lbl.grid(row=0, column=0, padx=10, pady=10)

year_entry = Entry(year_frame, width=10, font=('Arial', 14))
year_entry.grid(row=0, column=1, padx=10, pady=10)

buttons_frame = Frame(root, bg='black')
buttons_frame.pack()

show_calendar = Button(buttons_frame, text='Show Calendar', fg='green', font=('Arial', 12, 'bold'), command=display_calendar)
show_calendar.pack(side=LEFT, padx=10)

clear_button = Button(buttons_frame, text='Clear', fg='blue', font=('Arial', 12, 'bold'), command=clear_entries)
clear_button.pack(side=LEFT, padx=10)

exit_button = Button(buttons_frame, text='Exit', fg='purple', font=('Arial', 12, 'bold'), command=root.destroy)
exit_button.pack(side=LEFT, padx=10)

credits = Label(root, text='Powered by Tkinter', bg='black', fg='white', font=('Arial', 10))
credits.pack(side=BOTTOM, pady=10)

root.mainloop()


