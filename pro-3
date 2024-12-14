import json
from datetime import datetime

class ExpenseTracker:
    def _init_(self, file_name='expenses.json'):
        self.file_name = file_name
        self.expenses = self.load_expenses()

    def load_expenses(self):
        try:
            with open(self.file_name, 'r') as file:
                return json.load(file)
        except FileNotFoundError:
            return []

    def save_expenses(self):
        with open(self.file_name, 'w') as file:
            json.dump(self.expenses, file, indent=4)

    def add_expense(self, amount, description, category):
        expense = {
            'amount': amount,
            'description': description,
            'category': category,
            'date': datetime.now().strftime('%Y-%m-%d %H:%M:%S')
        }
        self.expenses.append(expense)
        self.save_expenses()

    def view_expenses(self):
        for expense in self.expenses:
            print(f"Amount: {expense['amount']}, Description: {expense['description']}, Category: {expense['category']}, Date: {expense['date']}")

    def category_wise_summary(self):
        summary = {}
        for expense in self.expenses:
            category = expense['category']
            summary[category] = summary.get(category, 0) + expense['amount']
        for category, total in summary.items():
            print(f"Category: {category}, Total: {total}")

    def monthly_summary(self):
        summary = {}
        for expense in self.expenses:
            month = expense['date'][:7]
            summary[month] = summary.get(month, 0) + expense['amount']
        for month, total in summary.items():
            print(f"Month: {month}, Total: {total}")

def main():
    tracker = ExpenseTracker()
    while True:
        print("\nExpense Tracker Menu:")
        print("1. Add Expense")
        print("2. View All Expenses")
        print("3. View Category-wise Summary")
        print("4. View Monthly Summary")
        print("5. Exit")
        choice = input("Enter your choice: ")

        try:
            if choice == '1':
                amount = float(input("Enter amount: "))
                description = input("Enter description: ")
                category = input("Enter category (e.g., food, transportation, entertainment): ")
                tracker.add_expense(amount, description, category)
                print("Expense added successfully!")
            elif choice == '2':
                tracker.view_expenses()
            elif choice == '3':
                tracker.category_wise_summary()
            elif choice == '4':
                tracker.monthly_summary()
            elif choice == '5':
                break
            else:
                print("Invalid choice. Please try again.")
        except ValueError as e:
            print(f"Error: {e}. Please enter valid inputs.")

if __name__ == "_main_":
    main()
