# TO-DO-List
Ever felt like you're drowning in tasks and need a lifeboat to rescue you? Well, look no further! Meet your new best friend, the To-Do List App 🦸‍♂️. This app is here to help you organize your life, one task at a time.  Whether you're tackling that mountain of homework 🏔️ or trying to remember if you fed your pet hamster 🐹, 



import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.util.ArrayList;

public class ToDoListApp {

    private JFrame frame;
    private JTextField taskField;
    private DefaultListModel<String> listModel;
    private JList<String> taskList;

    public ToDoListApp() {
        frame = new JFrame("My To-Do List");
        frame.setSize(400, 400);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLayout(new BorderLayout());

        taskField = new JTextField();
        JButton addButton = new JButton("Add Task");

        listModel = new DefaultListModel<>();
        taskList = new JList<>(listModel);

        JPanel topPanel = new JPanel(new BorderLayout());
        topPanel.add(taskField, BorderLayout.CENTER);
        topPanel.add(addButton, BorderLayout.EAST);

        frame.add(topPanel, BorderLayout.NORTH);
        frame.add(new JScrollPane(taskList), BorderLayout.CENTER);

        JButton deleteButton = new JButton("Delete Selected");
        frame.add(deleteButton, BorderLayout.SOUTH);

        // Add Task
        addButton.addActionListener(e -> {
            String task = taskField.getText().trim();
            if (!task.isEmpty()) {
                listModel.addElement(task);
                taskField.setText("");
            }
        });

        // Delete Task
        deleteButton.addActionListener(e -> {
            int selected = taskList.getSelectedIndex();
            if (selected != -1) {
                listModel.remove(selected);
            }
        });

        frame.setVisible(true);
    }

    public static void main(String[] args) {
        new ToDoListApp();
    }
}

