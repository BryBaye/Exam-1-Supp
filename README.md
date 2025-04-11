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

