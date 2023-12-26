import java.util.Scanner;

public class userLogin {
//username=yunus
//password=1234

    static int rightOfEntry = 3, balance1 = 1000;
    static boolean accountSituation = true, result;
    static Scanner input = new Scanner(System.in);
    static String userAction =
            "Balance inquiry------------------->1\n" +
                    "IBAN information------------------>2\n" +
                    "Withdraw money-------------------->3\n" +
                    "Transfer money to another account->4\n" +
                    "Quit application------------------>0", iban1 = "TR58 0010 2306 0062 0017 7858";


    public static void main(String[] args) {
//Login program
        if (accountSituation) {

            while (accountSituation) {
                if (rightOfEntry < 1) {
                    accountSituation = false;
                    break;
                }
                System.out.print("Username:");
                String userName = input.nextLine();
                System.out.print("Password:");
                String password = input.nextLine();
                boolean result = control(userName, password);
                if (result) {
                    break;
                }
            }

        }
        if (accountSituation == false) {
            System.out.println("Your account has been blocked.\nPlease contact with us.");
        }

    }


    public static boolean control(String userName, String password) {

        if (userName.equals("yunus") && password.equals("1234")) {
            System.out.println("Entering your account.");
            //BURAYAAAAAAAAAAAAa
            bank();
            return true;
        } else {
            if (rightOfEntry > 1) {
                System.out.println("Please try again");
            }
            rightOfEntry--;
            return false;
        }
    }

    public static void bank() {
        try {
            Thread.sleep(1500);
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
        System.out.print(userAction);
        int process = input.nextInt();
        switch (process) {
            case 1:
                System.out.println("Account balance = " + balance1);
                break;

            case 2:
                System.out.println("Account IBAN= " + iban1);
                break;

            case 3:
                System.out.print("Enter the amount of money you want to withdraw:");
                int withdrawMoney = input.nextInt();
                if (withdrawMoney <= balance1) {
                    balance1 -= withdrawMoney;
                    System.out.println("Take your money.\n" + "Available balance = " + balance1);
                } else {
                    System.out.println("--Insufficient funds--");
                }
                break;
            case 4:
                System.out.println("Enter the amount of money you want to send:");
                int moneySent = input.nextInt();
                if (moneySent <= balance1) {
                    System.out.print("Person to who money is send: ");
                    //iki tane scanner kullan
                    input.nextLine();
                    String toPerson = input.nextLine();
                    System.out.println("Money sent to account of " + toPerson);
                    break;

                } else {
                    System.out.println("Insufficient funds...");
                }
            default:
                break;
        }


    }
}
