import time


print("Welocome to the OCTA NET BANk ATM ")
print("\nYOur pin is one,two,three,four (in numericals)\n")
time.sleep(2)
pin = 1234
balance = 1000
transaction_history = []

# PIN Verification
entered_pin = int(input("Enter your PIN: "))
if entered_pin != pin:
    print("Incorrect PIN. Exiting.")
else:
    while True:
        print("\nATM Menu:")
        print("1. Account Balance Inquiry")
        print("2. Cash Withdrawal")
        print("3. Cash Deposit")
        print("4. PIN Change")
        print("5. Transaction History")
        print("6. Exit")

        choice = int(input("Select an option: "))

        if choice == 1:
            # Account Balance 
            print(f"Your current balance is: ${balance}")
            transaction_history.append(f"Balance Inquiry: ${balance}")

        elif choice == 2:
            # Withdrawal
            withdrawal_amount = int(input("Enter the amount to withdraw: "))
            if withdrawal_amount > balance:
                print("Insufficient funds.")
            else:
                balance -= withdrawal_amount
                print(f"You have withdrawn ${withdrawal_amount}. Your new balance is ${balance}.")
                transaction_history.append(f"Withdrawal: ${withdrawal_amount:}")

        elif choice == 3:
            # Deposit
            deposit_amount = float(input("Enter the amount to deposit: "))
            balance += deposit_amount
            print(f"You have deposited ${deposit_amount}. Your new balance is ${balance}.")
            transaction_history.append(f"Deposit: ${deposit_amount}")

        elif choice == 4:
            # PIN Change
            new_pin = int(input("Enter your new PIN: "))
            confirm_pin = int(input("Confirm your new PIN: "))
            if new_pin == confirm_pin:
                pin = new_pin
                print("Your PIN has been successfully changed.")
                transaction_history.append("PIN Changed")
            else:
                print("PINs do not match. PIN not changed.")

        elif choice == 5:
            # Transaction History
            print("Transaction History:")
            for tr in transaction_history:
                print(tr)

        elif choice == 6:
            # Exit
            print("Thank you for using the ATM. Goodbye!")
            break

        else:
            print("Invalid option. Please try again.")