import tkinter as tk
from tkinter import ttk


class School:
    def __init__(self, name, registration_fee, working_hours, location):
        self.name = name
        self.registration_fee = registration_fee
        self.working_hours = working_hours
        self.location = location


alhasad = School("alhasad School", 1700, "8 AM - 2 PM", "Amman")
alqadeh = School("alqadeh School", 1050, "7 AM - 2 PM", "Amman")
alnahda = School("alnahda School", 1000, "7 AM - 1 PM", "Irbid")
alnajah = School("alnajah School", 2000, "9 AM - 3 PM", "Irbid")
zean = School("zean School", 1100, "6 AM - 8 PM", "Madaba")
alia = School("aaa School", 1100, "6 AM - 8 PM", "Madaba")
moab = School("moab School", 2200, "6 AM - 1 PM", "alkark")
alalam = School("alalam School", 3200, "6 AM - 2 PM", "alkark")
zayed = School("zayed School", 1600, "7 AM - 2 PM", "tafila")
alnoor = School("alnoor School", 1800, "9 AM - 2 PM", "tafila")
alrooad = School("alrooad School", 1200, "9 AM - 4 PM", "alaqabeh")
aleman = School("aleman School", 1400, "7 AM - 3 PM", "alaqabeh")
alhaq = School("alhaq School", 1500, "8 AM - 3 PM", "maan")
alamani = School("alamani School", 1700, "6 AM - 1 PM", "maan")

schools = [alhasad,alqadeh,alnahda,alnajah, zean,alia, moab ,alalam, zayed, alnoor,alrooad,aleman, alhaq,alamani]


def show_school_details():
    selected_location = location_combobox.get()

    matching_schools = [school for school in schools if school.location == selected_location]

    if matching_schools:
        result_text = ""
        for school in matching_schools:
            result_text += f"School: {school.name}\nRegistration Fee: {school.registration_fee} JD\nWorking Hours: {school.working_hours}\n\n"

        result_label.config(text=result_text)

        with open("selected_school_details.txt", "w") as file:
            file.write(result_text)
    else:
        result_label.config(text="No schools found for the selected location.")



root = tk.Tk()
root.title("Private School Selection System")

location_label = tk.Label(root, text="Select a Location:")
location_combobox = ttk.Combobox(root, values=list(set([school.location for school in schools])))
location_label.pack(pady=10)
location_combobox.pack(pady=10)

show_details_button = tk.Button(root, text="Show School Details and Save", command=show_school_details)
show_details_button.pack(pady=10)
show_details_button = tk.Button(root, text="delete school", command=show_school_details)
show_details_button.pack(pady=10)
result_label = tk.Label(root, text="")
result_label.pack(pady=10)

root.mainloop()
