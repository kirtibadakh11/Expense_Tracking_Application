import java.util.ArrayList;
import java.util.Scanner;

class Expense {
    private String description;
    private double amount;

    public Expense(String description, double amount) {
        this.description = description;
        this.amount = amount;
    }

    public String getDescription() {
        return description;
    }

    public double getAmount() {
        return amount;
    }
}

class ExpenseTracker {
    private ArrayList<Expense> expenses;

    public ExpenseTracker() {
        this.expenses = new ArrayList<>();
    }

    public void addExpense(String description, double amount) {
        Expense expense = new Expense(description, amount);
        expenses.add(expense);
        System.out.println("Expense added successfully!");
    }

    public void viewExpenses() {
        System.out.println("Expenses:");
        for (Expense expense : expenses) {
            System.out.println("Description: " + expense.getDescription() + ", Amount: " + expense.getAmount());
        }
    }

    public void expenseSummaries() {
        double total = 0;
        for (Expense expense : expenses) {
            total += expense.getAmount();
        }
        System.out.println("Total Expenses: " + total);
    }
}

public class ExpenseTrackingApp {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ExpenseTracker expenseTracker = new ExpenseTracker();

        while (true) {
            System.out.println("\nExpense Tracking Application");
            System.out.println("1. Add Expense");
            System.out.println("2. View Expenses");
            System.out.println("3. Expense Summaries");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");

            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter expense description: ");
                    String description = scanner.nextLine();
                    System.out.print("Enter expense amount: ");
                    double amount = scanner.nextDouble();
                    expenseTracker.addExpense(description, amount);
                    break;
                case 2:
                    expenseTracker.viewExpenses();
                    break;
                case 3:
                    expenseTracker.expenseSummaries();
                    break;
                case 4:
                    System.out.println("Exiting...");
                    System.exit(0);
                default:
                    System.out.println("Invalid choice. Please enter a valid option.");
            }
        }
    }
}
