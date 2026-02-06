# 📝 PyTask Manager
**A Minimalist CLI Task Management System built with Python.**

---

## 🚀 Overview
[EN] **PyTask Manager** is a lightweight, command-line tool designed for developers who prefer staying in the terminal. It features persistent data storage, ensuring your tasks are saved even after closing the program.

[AR] **PyTask Manager** هو أداة بسيطة وسريعة لإدارة المهام من خلال سطر الأوامر. بيتميز بخاصية حفظ البيانات تلقائياً، يعني مهامك متسيفة ومش هتضيع حتى لو قفلت البرنامج.

---

## ✨ Key Features | المميزات
* **Persistent Storage:** Saves tasks to a local `.txt` file automatically. | **تخزين دائم:** بيحفظ المهام في ملف نصي خارجي تلقائياً.
* **Full Control:** Add, view, and remove tasks with simple numeric commands. | **تحكم كامل:** إضافة، عرض، وحذف المهام بأوامر رقمية بسيطة.
* **Clean CLI:** No messy UI, just focus on what needs to get done. | **واجهة بسيطة:** مفيش زحمة، بس ركز على اللي وراك.

---

## 🛠️ Tech Stack
- **Language:** Python 3.x
- **Storage:** Local File System (I/O Operations)

---

## 💻 The Source Code (main.py)
import os

def load_tasks():
    if os.path.exists("tasks.txt"):
        with open("tasks.txt", "r") as f:
            return [line.strip() for line in f.readlines()]
    return []

def save_tasks(tasks):
    with open("tasks.txt", "w") as f:
        for task in tasks:
            f.write(task + "\n")

def main():
    tasks = load_tasks()
    while True:
        print("\n1. View Tasks | 2. Add Task | 3. Remove Task | 4. Exit")
        choice = input("Your choice: ")
        if choice == '1':
            print("\n--- Current Tasks ---")
            for i, t in enumerate(tasks, 1): print(f"{i}. {t}")
        elif choice == '2':
            tasks.append(input("New Task: "))
            save_tasks(tasks)
        elif choice == '3':
            try:
                idx = int(input("Task # to delete: ")) - 1
                if 0 <= idx < len(tasks): 
                    tasks.pop(idx)
                    save_tasks(tasks)
                    print("Task removed!")
                else:
                    print("Invalid task number.")
            except ValueError: 
                print("Please enter a number!")
        elif choice == '4': 
            print("Goodbye!")
            break
        else: 
            print("Invalid choice!")

if __name__ == "__main__":
    main()
🚀 How to Run | طريقة التشغيل
Clone the repository:

Bash
git clone [https://github.com/eslamyasta4-lang/PyTask-Manager.git](https://github.com/eslamyasta4-lang/PyTask-Manager.git)
Navigate to the folder:

Bash
cd PyTask-Manager
Run the script:

Bash
python main.py
📅 Future Roadmap
[ ] Add priority levels (High/Medium/Low).

[ ] Add due dates for tasks.

[ ] Implement a search feature for long lists.

Crafted with 🐍 by eslamyasta4-lang
