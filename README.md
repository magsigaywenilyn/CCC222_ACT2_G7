import java.util.ArrayList;
import java.util.Scanner;

class SinglyLinkedList {
    Node head;

    void insertAtBeginning(int data) {
        Node newNode = new Node(data);
        newNode.next = head;
        head = newNode;
    }

    void insertAtEnd(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        Node last = head;
        while (last.next != null) {
            last = last.next;
        }
        last.next = newNode;
    }

    void display() {
        Node current = head;
        while (current != null) {

            System.out.print(current.data + " -> ");
            current = current.next;
        }
        System.out.println("null");
    }

    class Node {
        int data;
        Node next;

        public Node(int data) {
            this.data = data;
            this.next = null;
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        SinglyLinkedList sl = new SinglyLinkedList();
        ArrayList<Integer> arrayList = new ArrayList<>();
        while (true) {
            System.out.print("Enter a number: ");
            int number = scanner.nextInt();
            System.out.println("Options:");
            System.out.println("[1] Linked List");
            System.out.println("[2] Array");
            int choice = scanner.nextInt();
            scanner.nextLine();
            switch (choice) {
                case 1:
                    System.out.println("Options");
                    System.out.println("[1]insert at Beginning");
                    System.out.println("[2]insert at End");
                    int linkedListChoice = scanner.nextInt();
                    scanner.nextLine();
                    switch (linkedListChoice) {
                        case 1:
                            sl.insertAtBeginning(number);
                            System.out.print("Linked list after insertion: ");
                            sl.display();
                            break;
                        case 2:
                            sl.insertAtEnd(number);
                            System.out.print("Linked list after insertion: ");
                            sl.display();
                            break;
                        default:
                            System.out.println("Invalid choice. Please enter 1 or 2.");
                    }
                    break;
                case 2:
                    arrayList.add(number);
                    System.out.println("Array after insertion:" + arrayList);
                    break;
                default:
                    System.out.println("Invalid choice. Please enter 1 or 2.");
            }
            String proceed;
            while (true) {
                System.out.println("Proceed? [yes/no]: ");
                proceed = scanner.next().toLowerCase();

                if (proceed.equals("yes")) {
                    break;
                } else if (proceed.equals("no")) {
                    System.out.println("result:");
                    System.out.print("Link list: ");
                    sl.display();
                    System.out.println("array list: "+arrayList);
                    System.out.println("Terminating program...");
                    scanner.close();
                    return;
                } else {
                    System.out.println("Invalid input. Please enter 'yes' or 'no'.");
                }
            }
        }
    }
}
