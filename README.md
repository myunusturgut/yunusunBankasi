import java.util.Scanner;

public class banka {
    public static void main(String[] args) {


        String kullaniciislemleri = "Bakiye sorgulamak için----------->1\n" +
                "IBAN görüntülemek için----------->2\n" +
                "Para çekmek için----------------->3\n" +
                "Başka hesaba para transferi için->4\n" +
                "Uygulamadan çıkmak için---------->0";

        String user1 = "yunus";
        String user2 = "hamza";
        String sifre1 = "1234";
        String sifre2 = "4321";
        String iban1 = "TR58 0010 2306 0062 0017 7858";
        String iban2 = "TR31 6485 6548 6510 0003 0059";


        int bakiye1 = 1000;
        int bakiye2 = 2200;


        Scanner scanner = new Scanner(System.in);
        System.out.print("Kullanıcı adını giriniz: ");
        String user = scanner.nextLine();

        System.out.print("Şifrenizi giriniz: ");
        String sifre = scanner.nextLine();

        if (user.equals(user1) && sifre.equals(sifre1)) {
            System.out.println("Yunus hesabına giriş yapılıyor...");

            // Delay için mili saniye türünden yazılır
            try {
                Thread.sleep(3000);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }

            System.out.print(kullaniciislemleri);
            //System.out.println();
            int islem = scanner.nextInt();
            switch (islem) {
                case 1:
                    System.out.println("bakiye miktarı = " + bakiye1);
                    break;

                case 2:
                    System.out.println("Hesap ibanınız = " + iban1);
                    break;

                case 3:
                    System.out.print("Çekmek istediğiniz para miktarını giriniz:");
                    int paracekim = scanner.nextInt();
                    if (paracekim <= bakiye1) {
                        bakiye1 -= paracekim;
                        System.out.println("Paranızı alınız.\n" + "Kalan bakiyeniz = " + bakiye1);
                    } else {
                        System.out.println("--Yetersiz bakiye--");
                    }
                    break;
                case 4:
                    System.out.println("Göndermek istediğiniz para miktarını girin");
                    int gonderilenPara = scanner.nextInt();
                    if (gonderilenPara <= bakiye1) {
                        System.out.print("Gönderilecek kişi: ");
                        //iki tane scanner kullan
                        scanner.nextLine();
                        String gonderilenkisi = scanner.nextLine();
                        System.out.println(gonderilenkisi + " hesabına para gönderildi.");
                        break;

                    } else {
                        System.out.println("Yetersiz bakiye");
                    }
                default:
                    break;
            }


            //hamzanın hesap------------------------------------------------
        } else if (user.equals(user2) && sifre.equals(sifre2)) {
            System.out.print("Hamza hesabına giriş yapıldı.");
        } else {
            System.out.println("Kullanıcı adı veya şifreniz yanlış.");
        }


    }
}
