# Exam-1-Supp
public class DayNode {
    private String date;
    private String[] students;
    private DayNode next;

    public DayNode(String date, String[] students) {
        this.date = date;
        this.students = students;
        this.next = null;

public class DayNode {
    private String date;
    private String[] students;
    private DayNode next;

    public DayNode(String date, String[] students) {
        this.date = date;
        this.students = students;
        this.next = null;
    }

    public String getDate() {
        return date;
    }

    public String[] getStudents() {
        return students;
    }

    public DayNode getNext() {
        return next;
    }

    public void setNext(DayNode next) {
        this.next = next;
    }

    @Override
    public String toString() {
        return "Date: " + date + ", Students: " + String.join(", ", students);
    }
}

public class StudentNode {
    private String name;
    private int classesAttended;
    private String explanations;
    private StudentNode next;

    public StudentNode(String name) {
        this.name = name;
        this.classesAttended = 0;
        this.explanations = "";
        this.next = null;
    }

    public String getName() {
        return name;
    }

    public int getClassesAttended() {
        return classesAttended;
    }

    public void incrementClassesAttended() {
        classesAttended++;
    }

    public String getExplanations() {
        return explanations;
    }

    public void addExplanation(String explanation) {
        if (!explanations.isEmpty()) {
            explanations += "; ";
        }
        explanations += explanation;
    }

    public StudentNode getNext() {
        return next;
    }

    public void setNext(StudentNode next) {
        this.next = next;
    }

    @Override
    public String toString() {
        return name + "," + classesAttended + "," + explanations;
    }
}
import java.io.*;
import java.util.*;


public class AttendanceProcessor {

   
    public static DayNode buildAttendanceList(String filename) throws IOException {
        BufferedReader reader = new BufferedReader(new FileReader(filename));
        DayNode head = null, tail = null;
        String line;
        while ((line = reader.readLine()) != null) {
            String[] parts = line.split(",");
            String date = parts[0];
            String[] students = Arrays.copyOfRange(parts, 1, parts.length);
            DayNode node = new DayNode(date, students);
            if (head == null) {
                head = node;
                tail = node;
            } else {
                tail.setNext(node);
                tail = node;
            }
        }
        reader.close();
        return head;
    }

    
    public static StudentNode buildStudentList(DayNode head) {
        Map<String, StudentNode> studentMap = new HashMap<>();
        DayNode current = head;
        while (current != null) {
            for (String student : current.getStudents()) {
                studentMap.putIfAbsent(student, new StudentNode(student));
                studentMap.get(student).incrementClassesAttended();
            }
            current = current.getNext();
        }

        StudentNode headStudent = null, tail = null;
        for (StudentNode node : studentMap.values()) {
            if (headStudent == null) {
                headStudent = node;
                tail = node;
            } else {
                tail.setNext(node);
                tail = node;
            }
        }
        return headStudent;
    }

   
    public static void applyExcusedAbsences(StudentNode head, String filename) throws IOException {
        BufferedReader reader = new BufferedReader(new FileReader(filename));
        String line;
        while ((line = reader.readLine()) != null) {
            String[] parts = line.split(",");
            String name = parts[0];
            String date = parts[1];
            String explanation = parts[2];

            StudentNode current = head;
            while (current != null) {
                if (current.getName().equals(name)) {
                    current.incrementClassesAttended();
                    current.addExplanation(date + ": " + explanation);
                    break;
                }
                current = current.getNext();
            }
        }
        reader.close();
    }

   
    public static void writeStudentList(StudentNode head, String filename) throws IOException {
        BufferedWriter writer = new BufferedWriter(new FileWriter(filename));
        StudentNode current = head;
        while (current != null) {
            writer.write(current.toString());
            writer.newLine();
            current = current.getNext();
        }
        writer.close();
    }
}
