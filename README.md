# Exam-1-Supp
public class DayNode {
    private String date;
    private String[] students;
    private DayNode next;

    public DayNode(String date, String[] students) {
        this.date = date;
        this.students = students;
        this.next = null;
