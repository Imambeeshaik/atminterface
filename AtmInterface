import java.util.HashMap;
import java.util.Map;

class User {
    private String userId;
    private String pin;
    private double balance;

    public User(String userId, String pin, double balance) {
        this.userId = userId;
        this.pin = pin;
        this.balance = balance;
    }

    public String getUserId() {
        return userId;
    }

    public String getPin() {
        return pin;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }
}

class Transaction {
    public static void withdraw(User user, double amount) {
        if (amount > user.getBalance()) {
            System.out.println("Insufficient funds.");
        } else {
            user.setBalance(user.getBalance() - amount);
            System.out.println("Withdrawn: $" + amount);
        }
    }

    public static void deposit(User user, double amount) {
        user.setBalance(user.getBalance() + amount);
        System.out.println("Deposited: $" + amount);
    }

    public static void transfer(User userFrom, User userTo, double amount) {
        if (amount > userFrom.getBalance()) {
            System.out.println("Insufficient funds.");
        } else {
            userFrom.setBalance(userFrom.getBalance() - amount);
            userTo.setBalance(userTo.getBalance() + amount);
            System.out.println("Transferred: $" + amount);
        }
    }
}

class History {
    private static Map<String, String> transactionHistory = new HashMap<>();

    public static void addTransaction(String userId, String transaction) {
        transactionHistory.put(userId, transaction);
    }

    public static void displayHistory(String userId) {
        String transaction = transactionHistory.get(userId);
        System.out.println("Transaction History for User: " + userId);
        System.out.println(transaction != null ? transaction : "No transactions yet.");
    }
}

class ATM {
    private static Map<String, User> users = new HashMap<>();

    public static void addUser(User user) {
        users.put(user.getUserId(), user);
    }

    public static boolean authenticate(String userId, String pin) {
        User user = users.get(userId);
        return user != null && user.getPin().equals(pin);
    }

    public static void startATM(String userId) {
        if (authenticate(userId, users.get(userId).getPin())) {
            System.out.println("Welcome, " + userId + "!");
            // ATM functionality unlocked
        } else {
            System.out.println("Authentication failed.");
        }
    }
}

public class AtmInterface {
    public static void main(String[] args) {
        // Create users
        User user1 = new User("user1", "1234", 1000.0);
        User user2 = new User("user2", "5678", 500.0);

        // Add users to ATM
        ATM.addUser(user1);
        ATM.addUser(user2);

        // Start ATM
        String userId = "user1"; // Example user
        String pin = "1234"; // Example PIN
        ATM.startATM(userId);

        // Perform transactions
        Transaction.withdraw(user1, 200.0);
        Transaction.deposit(user1, 300.0);
        Transaction.transfer(user1, user2, 150.0);

        // Display transaction history
        History.displayHistory(userId);
    }
}
