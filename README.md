import java.util.Scanner;

public class Restaurant {

    private static final String[] APPETIZERS = {
            "Classic Caesar Salad", "Crispy Calamari", "Stuffed Mushrooms", "Spinach and Artichoke Dip", "Shrimp Cocktail"
    };
    private static final String[] ENTREES = {
            "Grilled Salmon", "Chicken Alfredo Pasta", "Steak Frites", "Vegetable Stir Fry", "BBQ Baby Back Ribs"
    };
    private static final String[] DESSERTS = {
            "Chocolate Lava Cake", "New York Cheesecake", "Apple Pie a la Mode", "Tiramisu", "Mixed Berry Sorbet"
    };
    private static final double[] MENU_PRICES = {
            7.99, 9.99, 8.99, 7.49, 10.99,
            18.99, 16.99, 24.99, 14.99, 19.99,
            7.99, 6.99, 7.49, 7.99, 6.49
    };
    private static final int[] ORDER_COUNT = new int[15];
    private static int totalOrders = 0;
    private static double totalRevenue = 0;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (totalOrders < 20) {
            System.out.println("Welcome to our restaurant drive through! Please select only one item from the menu:");
            displayMenu();
            System.out.print("Please enter the number of your menu item selection: ");
            String input = scanner.nextLine();

            try {
                int selection = Integer.parseInt(input);
                if (selection >= 1 && selection <= 15) {
                    totalOrders++;
                    double price = MENU_PRICES[selection - 1];
                    totalRevenue += price;
                    ORDER_COUNT[selection - 1]++;
                    String menuItem = getMenuItem(selection - 1);
                    System.out.println("Order placed for: " + menuItem);
                    System.out.println("Thank you for ordering the " + menuItem + "! Your total is: $" + price + "\n");
                } else {
                    System.out.println("Invalid selection. Please try again.\n");
                }
            } catch (NumberFormatException e) {
                System.out.println("Invalid input. Please enter a number.\n");
            }
        }

        displaySummary();
        scanner.close();
    }

    private static void displayMenu() {
        System.out.println("Menu:");
        displayCategory("Appetizers", APPETIZERS, 0);
        displayCategory("Entrees", ENTREES, 5);
        displayCategory("Desserts", DESSERTS, 10);
        System.out.println();
    }

    private static void displayCategory(String category, String[] items, int offset) {
        System.out.println(category + ":");
        for (int i = 0; i < items.length; i++) {
            System.out.println((i + 1 + offset) + ". " + items[i] + " - $" + MENU_PRICES[i + offset]);
        }
        System.out.println();
    }

    private static String getMenuItem(int index) {
        if (index < 5) return APPETIZERS[index];
        if (index < 10) return ENTREES[index - 5];
        return DESSERTS[index - 10];
    }

    private static void displaySummary() {
        System.out.println("Summary:");
        System.out.println("Total money made: $" + totalRevenue);
        for (int i = 0; i < 15; i++) {
            double percentage = ((double) ORDER_COUNT[i] / 20.0) * 100;
            System.out.println(getMenuItem(i) + ": " + percentage + "% sales, ordered " + ORDER_COUNT[i] + " times");
        }
    }
}
