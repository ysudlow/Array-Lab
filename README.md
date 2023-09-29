# Array-Lab

import java.text.DecimalFormat;
import java.util.Arrays;
import java.util.Random;

public class FastFoodRestaurant {
    public static void main(String[] args) {
        // Create a menu with 5 appetizers, 5 entrees, and 5 desserts
        String[] menu = {
            "Chicken McNuggets (6 pieces)",
            "Mozzarella Sticks (4 pieces)",
            "Loaded Potato Skins (3 pieces)",
            "Onion Rings (Regular)",
            "Fried Calamari (Small)",
            "Cheeseburger (Single)",
            "Chicken Sandwich (Classic)",
            "Grilled Cheese Sandwich (Regular)",
            "Spaghetti with Meatballs (Large)",
            "BBQ Ribs (Half Rack)",
            "Chocolate Sundae",
            "Apple Pie",
            "Fudge Brownie",
            "Soft Serve Ice Cream Cone",
            "Milkshake (Small)"
        };

        // Create an array to store the prices corresponding to the menu items
        double[] prices = {
            4.99,  // Chicken McNuggets
            3.49,  // Mozzarella Sticks
            5.99,  // Loaded Potato Skins
            2.99,  // Onion Rings
            6.99,  // Fried Calamari
            3.49,  // Cheeseburger
            4.99,  // Chicken Sandwich
            2.99,  // Grilled Cheese Sandwich
            7.99,  // Spaghetti with Meatballs
            9.99,  // BBQ Ribs
            2.49,  // Chocolate Sundae
            1.99,  // Apple Pie
            2.99,  // Fudge Brownie
            1.49,  // Soft Serve Ice Cream Cone
            3.99   // Milkshake (Small)
        };

        // Initialize an array to store the number of times each item is ordered
        int[] orderCount = new int[menu.length];

        // Initialize variables to store total money and order count
        double totalMoney = 0;
        int totalOrders = 20;

        // Generate a welcome message
        System.out.println("Welcome to Mc Wendy's! Please order one item from our menu. Thank you!");

        // Display the menu with prices
        System.out.println("\nHere's our menu:");
        for (int i = 0; i < menu.length; i++) {
            System.out.println((i + 1) + ". " + menu[i] + " - $" + prices[i]);
        }

        // Randomly generate and process 20 orders
        Random rand = new Random();
        for (int i = 0; i < totalOrders; i++) {
            int randomIndex = rand.nextInt(menu.length);
            orderCount[randomIndex]++;
            totalMoney += prices[randomIndex];
        }

        // Display the summary
        System.out.println("\nOrder Summary:");
        DecimalFormat df = new DecimalFormat("0.00");
        for (int i = 0; i < menu.length; i++) {
            double percentage = ((double) orderCount[i] / totalOrders) * 100;
            System.out.println(menu[i] + ": " + orderCount[i] + " orders (" + df.format(percentage) + "%)");
        }

        // Display the total money made
        System.out.println("Total Money Made: $" + totalMoney);
    }
}
