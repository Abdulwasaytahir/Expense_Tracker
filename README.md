# Expense_Tracker
# Simple Personal Expense Tracker

expenses = []

def add_expense():
    name = input("Expense name: ")
    amount = float(input("Amount (PKR): "))
    expenses.append({"name": name, "amount": amount})
    print(f"Added: {name} - Rs.{amount}\n")

def show_expenses():
    if not expenses:
        print("No expenses recorded yet.\n")
        return
    print("\n------ Your Expenses ------")
    total = 0
    for i, e in enumerate(expenses, start=1):
        print(f"{i}. {e['name']} - Rs.{e['amount']}")
        total += e['amount']
    print("----------------------------")
    print(f"Total Spent: Rs.{total}\n")

def delete_expense():
    show_expenses()
    if not expenses:
        return
    try:
        index = int(input("Enter expense number to delete: ")) - 1
        deleted = expenses.pop(index)
        print(f"Deleted: {deleted['name']} - Rs.{deleted['amount']}\n")
    except (ValueError, IndexError):
        print("Invalid choice!\n")

while True:
    print("=== Expense Tracker Menu ===")
    print("1. Add Expense")
    print("2. Show All Expenses")
    print("3. Delete Expense")
    print("4. Exit")

    choice = input("Choose an option (1-4): ")

    if choice == "1":
        add_expense()
    elif choice == "2":
        show_expenses()
    elif choice == "3":
        delete_expense()
    elif choice == "4":
        print("Goodbye!")
        break
    else:
        print("Invalid option! Try again.\n")

