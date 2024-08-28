import java.time.LocalDate;
import java.time.Month;

public class FinancialYearAndQuarter {
    public static void main(String[] args) {
        // Get the current date
        LocalDate currentDate = LocalDate.now();

        // Determine the financial year
        int year = currentDate.getYear();
        Month month = currentDate.getMonth();

        // Financial year typically starts in April and ends in March
        int financialYear;
        if (month.isBefore(Month.APRIL)) {
            financialYear = year - 1;
        } else {
            financialYear = year;
        }

        // Determine the financial quarter
        int quarter;
        if (month.isBefore(Month.JULY)) {
            quarter = 1;
        } else if (month.isBefore(Month.OCTOBER)) {
            quarter = 2;
        } else if (month.isBefore(Month.JANUARY)) {
            quarter = 3;
        } else {
            quarter = 4;
        }

        // Output the financial year and quarter
        System.out.println("Financial Year: " + financialYear + "-" + (financialYear + 1));
        System.out.println("Quarter: Q" + quarter);
    }
}