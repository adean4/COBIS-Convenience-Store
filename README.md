package adean4;

import java.util.ArrayList;
import java.util.Scanner;
public class Main {

    public static void main(String[] args) {
        // write your code here
        //creating ArrayLists
        ArrayList<String> products = new ArrayList<String>();
        ArrayList<Double> prices = new ArrayList<Double>();
        ArrayList<String> CustomerOrder = new ArrayList<String>();
        ArrayList<Integer> ProductQuantity = new ArrayList<Integer>();

        Scanner input = new Scanner(System.in); // input

        //Adding products and prices
        products.add("Red-Hot Spicy Doritos");
        prices.add(2.99);
        products.add("Cool Ranch Doritos");
        prices.add(2.99);
        products.add("Sunflower Seeds");
        prices.add(0.99);
        products.add("Peanuts");
        prices.add(0.99);
        products.add("Coke");
        prices.add(0.99);
        products.add("Diet Coke");
        prices.add(0.99);
        products.add("Pepsi");
        prices.add(0.99);
        products.add("Five Hour Energy");
        prices.add(3.99);
        products.add("MacBook Charger");
        prices.add(120.00);
        products.add("Dell Charger");
        prices.add(50.00);


        System.out.println("Welcome to the Convenience Store");

        {

            System.out.println(
                    "\n0 :  Red-Hot Spicy Doritos" +
                            "\n1 :  Cool Ranch Doritos" +
                            "\n2 :  Sunflower Seeds" +
                            "\n3 :  Peanuts" +
                            "\n4 :  Coke" +
                            "\n5 :  Diet Coke" +
                            "\n6 :  Pepsi" +
                            "\n7 :  Five Hour Energy" +
                            "\n8 :  MacBook Charger" +
                            "\n9 : Dell Charger");
            Scanner response = new Scanner(System.in);
            String cusInput;
            StringBuilder output = new StringBuilder();
            double orderTotal;
            double grandTotal = 0;


            System.out.println("Enter customer name or type CLOSE if finished for the day");
            while (!(cusInput = response.nextLine()).equalsIgnoreCase("CLOSE")) {
                output.append(cusInput);
                orderTotal = 0;
                do {

                    System.out.println("Snacks: {0 Red-Hot Spicy Doritos}, {1 Cool Ranch Doritos}, {2 Sunflower Seeds}, {3 Peanuts}");
                    System.out.println("Drinks: {4 Coke}, {5 Diet Coke}, {7 Pepsi}, {7 Five Hour Energy}");
                    System.out.println("Electronics: {8 MacBook Charger}, {9 Dell Charger}");
                    System.out.println("Enter the ITEM NUMBER of the product to add to transaction. (Enter Code:500 to close transaction): ");


                    cusInput = response.nextLine();
                    for (String prod : products) {
                        if (Integer.parseInt(cusInput) == products.indexOf(prod)) {
                            products.get(products.indexOf(prod));
                            orderTotal += prices.get(products.indexOf(prod));
                            String itemname = products.get(Integer.parseInt(cusInput));
                            output.append("\n").append(itemname);
                            if (!CustomerOrder.contains(cusInput)) {
                                CustomerOrder.add(cusInput);
                                ProductQuantity.add(1);
                            } else {
                                int indexnum = CustomerOrder.indexOf(cusInput);
                                ProductQuantity.set(indexnum, ProductQuantity.get(indexnum) + 1);
                            }
                            break;
                        }
                    }
                } while (!cusInput.equalsIgnoreCase("500"));
                output.append(" \n \t\t\t").append(orderTotal).append("\n");
                grandTotal += orderTotal;

                System.out.println("Enter the name of the next customer to start next transaction.(Type CLOSE to close store for final counts): ");
            }
            System.out.println("The Convenience Store is now Closed ");

            System.out.println("\n" + "Receipts per Customer Today: \n " + output);

            System.out.println("Total Inventory Sold Today: ");
            System.out.println(" ");

            for (String invquantity : CustomerOrder) {

                System.out.println("Item Number " + invquantity + ":" + " [" + ProductQuantity.get(CustomerOrder.indexOf(invquantity)) + "]");
            }

            System.out.println(" ");
            System.out.println("Grand Total: $" + grandTotal);

        }
    }
}

