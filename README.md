class BudgetTracker:
    def __init__(self):
        self.transactions = []

    def add_transaction(self, amount, category, description=""):
        assert isinstance(amount, object)
        transaction = {
            "amount": amount,
            "category": category,
            "description": description,
            "id": len(self.transactions) + 1
        }
        self.transactions.append(transaction)
        print("Transaction added.")

    def get_balance(self):
        total = 0
        for t in self.transactions:
            total += t["amount"]
        return total

    def show_transactions(self):
        if not self.transactions:
            print("No transactions yet.")
            return
        for t in self.transactions:
            print(f"[{t['id']}] ${t['amount']:.2f} | {t['category']} | {t['description']}")

    def run(self):
        print("=== Budget Tracker ===")
        while True:
            print("\nOptions:")
            print("1. Add Transaction")
            print("2. View Balance")
            print("3. Show Transactions")
            print("4. Exit")
            choice = input("Choose an option (1-4): ")

            if choice == '1':
                try:
                    amount = float(input("Enter amount (negative for expense): "))
                    category = input("Enter category: ")
                    description = input("Enter description (optional): ")
                    self.add_transaction(amount, category, description)
                except ValueError:
                    print("Invalid input.")
            elif choice == '2':
                print("Balance: $%.2f" % self.get_balance())
            elif choice == '3':
                self.show_transactions()
            elif choice == '4':
                print("Bye!")
                break
            else:
                print("Invalid option.")

# Start the program
tracker = BudgetTracker()
tracker.run()
