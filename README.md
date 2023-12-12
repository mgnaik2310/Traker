class Expense {
  constructor(amount, description, category) {
    this.amount = amount;
    this.description = description;
    this.category = category;
  }

  toString() {
    return `${this.amount}-${this.description}-${this.category}`;
  }
}

class ExpenseTracker {
  constructor() {
    this.expenses = [];
  }

  addExpense(expense) {
    this.expenses.push(expense);
    console.log("Expense added successfully.");
  }

  editExpense(index, newExpense) {
    if (index >= 0 && index < this.expenses.length) {
      this.expenses[index] = newExpense;
      console.log("Expense edited successfully.");
    } else {
      console.log("Invalid index. Expense not edited.");
    }
  }

  deleteExpense(index) {
    if (index >= 0 && index < this.expenses.length) {
      const deletedExpense = this.expenses.splice(index, 1)[0];
      console.log(`Expense deleted successfully: ${deletedExpense}`);
    } else {
      console.log("Invalid index. Expense not deleted.");
    }
  }

  displayExpenses() {
    console.log("Current Expenses:");
    this.expenses.forEach((expense, index) => {
      console.log(`${index + 1}. ${expense}`);
    });
  }
}

const tracker = new ExpenseTracker();

function main() {
  while (true) {
    console.log("\nOptions:");
    console.log("1. Add Expense");
    console.log("2. Edit Expense");
    console.log("3. Delete Expense");
    console.log("4. Display Expenses");
    console.log("5. Exit");

    const choice = prompt("Enter your choice: ");

    if (choice === "1") {
      const amount = prompt("Enter expense amount: ");
      const description = prompt("Enter expense description: ");
      const category = prompt("Enter expense category: ");
      const newExpense = new Expense(amount, description, category);
      tracker.addExpense(newExpense);
    } else if (choice === "2") {
      tracker.displayExpenses();
      const index = prompt("Enter the index of the expense to edit: ") - 1;
      const amount = prompt("Enter new expense amount: ");
      const description = prompt("Enter new expense description: ");
      const category = prompt("Enter new expense category: ");
      const newExpense = new Expense(amount, description, category);
      tracker.editExpense(index, newExpense);
    } else if (choice === "3") {
      tracker.displayExpenses();
      const index = prompt("Enter the index of the expense to delete: ") - 1;
      tracker.deleteExpense(index);
    } else if (choice === "4") {
      tracker.displayExpenses();
    } else if (choice === "5") {
      console.log("Exiting the Expense Tracker. Goodbye!");
      break;
    } else {
      console.log("Invalid choice. Please enter a valid option.");
    }
  }
}

main();
