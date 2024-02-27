class User:
    def __init__(self, user_id, pin):
        self.user_id = user_id
        self.pin = pin


class Transaction:
    def __init__(self, amount, transaction_type):
        self.amount = amount
        self.transaction_type = transaction_type


class ATM:
    def __init__(self, users):
        self.users = users

    def authenticate_user(self, user_id, pin):
        for user in self.users:
            if user.user_id == user_id and user.pin == pin:
                return True
        return False

    def display_menu(self):
        print("1. Transaction History")
        print("2. Withdraw")
        print("3. Deposit")
        print("4. Transfer")
        print("5. Quit")

    def perform_transaction(self, user_id):
        while True:
            self.display_menu()
            choice = input("Enter your choice: ")
            if choice == '1':
                self.show_transaction_history(user_id)
            elif choice == '2':
                amount = float(input("Enter amount to withdraw: "))
                self.withdraw(user_id, amount)
            elif choice == '3':
                amount = float(input("Enter amount to deposit: "))
                self.deposit(user_id, amount)
            elif choice == '4':
                print("Transfer feature is not implemented yet.")
            elif choice == '5':
                print("Thank you for using our ATM.")
                break
            else:
                print("Invalid choice.")

    def show_transaction_history(self, user_id):
        print("Transaction History:")
        # Fetch and display transaction history for the user

    def withdraw(self, user_id, amount):
        print(f"Withdrawing {amount} from user {user_id}")
        # Implement withdrawal logic

    def deposit(self, user_id, amount):
        print(f"Depositing {amount} to user {user_id}")
        # Implement deposit logic


# Sample usage
def main():
    users = [User("1234", "5678")]  # Example user
    atm = ATM(users)
    user_id = input("Enter user ID: ")
    pin = input("Enter PIN: ")

    if atm.authenticate_user(user_id, pin):
        print("Authentication successful. Welcome!")
        atm.perform_transaction(user_id)
    else:
        print("Authentication failed. Please try again.")


if __name__ == "__main__":
    main()
