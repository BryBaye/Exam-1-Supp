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
