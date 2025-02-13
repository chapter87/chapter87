# Function to calculate tax based on income
def calculate_tax(income):
    """Calculates tax and determines the tax band based on income."""
    if income <= 20000:
        return 0, "Personal Allowance"
    elif income <= 100000:
        return 0.2 * (income - 20000), "Basic Rate"
    else:
        return 0.45 * (income - 100000) + 0.2 * (100000 - 20000), "Additional Rate"
# Function to print the payslip

def print_payslip(name, organisation, income, tax_band, tax, net_pay):
    """Prints the payslip for the employee."""
    print("\n--- Payslip ---")
    print(f"Employee Name: {name}")
    print(f"Organisation: {organisation}")
    print(f"Income: £{income:,.2f}")
    print(f"Tax Band: {tax_band}")
    print(f"Income Tax: £{tax:,.2f}")
    print(f"Net Pay: £{net_pay:,.2f}")
# Main program
def main():
    """Main function to collect employee details and generate a payslip."""
    print("Welcome to the Tax Calculation Software!")
# Ask for employee details
    
    while True:
        name = input("Enter the employee's full name: ").strip()
        organisation = input("Enter the organisation they work for: ").strip()
        
        while True:
            try:
                income = float(input("Enter the employee's income: £").strip())
                if income < 0:
                    print("Income cannot be negative. Please enter a valid amount.")
                    continue
                break
            except ValueError:
                print("Invalid input. Please enter a numeric value for income.")
 # Calculate tax, tax band, and net pay
        tax, tax_band = calculate_tax(income)
        net_pay = income - tax
 # Print the payslip
        print_payslip(name, organisation, income, tax_band, tax, net_pay)
# Ask if the user wants to add another employee
        another = input("Do you want to add another employee? (yes/no): ").strip().lower()
        if another != "yes":
            break
    
    print("Thank you for using the Tax Calculation Software. Goodbye!")
Run the program
if __name__ == "__main__":
    main()

