import java.util.ArrayList;
import java.util.Scanner;


class Task {
    private String title;
    private String description;
    private boolean isCompleted;

    // Constructor
    public Task(String title, String description) {
        this.title = title;
        this.description = description;
        this.isCompleted = false;
    }

    // Getters and setters
    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getDescription() {
        return description;
    }

    public void setDescription(String description) {
        this.description = description;
    }

    public boolean isCompleted() {
        return isCompleted;
    }

    public void setCompleted(boolean isCompleted) {
        this.isCompleted = isCompleted;
    }

    // Method to display task details
    public void displayTask() {
        System.out.println("Title: " + title);
        System.out.println("Description: " + description);
        System.out.println("Status: " + (isCompleted ? "Completed" : "Not Completed"));
    }
}

// TaskManager class to manage a list of tasks
class TaskManager {
    private ArrayList<Task> tasks;

    // Constructor
    public TaskManager() {
        tasks = new ArrayList<>();
    }

    // Method to add a new task
    public void addTask(Task task) {
        tasks.add(task);
    }

    // Method to update an existing task
    public void updateTask(int index, String title, String description, boolean isCompleted) {
        if (index >= 0 && index < tasks.size()) {
            Task task = tasks.get(index);
            task.setTitle(title);
            task.setDescription(description);
            task.setCompleted(isCompleted);
        } else {
            System.out.println("Invalid task index.");
        }
    }

    // Method to display all tasks
    public void displayAllTasks() {
        if (tasks.isEmpty()) {
            System.out.println("No tasks to display.");
            return;
        }
        for (int i = 0; i < tasks.size(); i++) {
            System.out.println("Task " + (i + 1) + ":");
            tasks.get(i).displayTask();
            System.out.println();
        }
    }
}

// Main class to run the task management system
public class TaskManagementSystem {
    public static void main(String[] args) {
        TaskManager taskManager = new TaskManager();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Task Management System:");
            System.out.println("1. Add Task");
            System.out.println("2. Update Task");
            System.out.println("3. Display All Tasks");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); 

            switch (choice) {
                case 1:
                    // Add Task
                    System.out.print("Enter task title: ");
                    String title = scanner.nextLine();
                    System.out.print("Enter task description: ");
                    String description = scanner.nextLine();
                    Task newTask = new Task(title, description);
                    taskManager.addTask(newTask);
                    break;
                case 2:
                    // Update Task
                    System.out.print("Enter task index to update: ");
                    int index = scanner.nextInt() ;
                    scanner.nextLine(); 
                    System.out.print("Enter new task title: ");
                    title = scanner.nextLine();
                    System.out.print("Enter new task description: ");
                    description = scanner.nextLine();
                    System.out.print("Is the task completed? (true/false): ");
                    boolean isCompleted = scanner.nextBoolean();
                    taskManager.updateTask(index, title, description, isCompleted);
                    break;
                case 3:
                    // Displey All Tasks
                    taskManager.displayAllTasks();
                    break;
                case 4:
                    // Exit
                    System.out.println("Exiting.........................................................................................................!");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid option. Please try try try again.");
            }
        }
    }
}
