import java.util.Random;
import java.util.Scanner;


public class Main {

    public static void main(String[] args) {
        char[] doska = new char[]{' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' '};
        int i = 0;
        while (doska[i] == ' ') {
            PomocneFunkcie.vypisDosku(doska);

            System.out.println();
            System.out.println("-----------------------");


            PomocneFunkcie.tahPocitaca(doska);
            System.out.println();
            PomocneFunkcie.vysledokHry(doska);

            PomocneFunkcie.vypisDosku(doska);

            System.out.println();
            System.out.println("-----------------------");

            TahCloveka.tahCloveka(doska);
            System.out.println();
            PomocneFunkcie.vysledokHry(doska);

            System.out.println();
            System.out.println("-----------------------");

            i++;
        }
    }
}







//vytvorit hernu dosku = dvojdimenzionalne pole
// urcit pocitacu x a mne o
//vygenerovat vlozenie znaku do






import java.util.Random;
import java.util.Scanner;


public abstract class PomocneFunkcie {


    public static void vypisDosku(char[] localDoska) {
        for (int i = 0; i < localDoska.length; i++) {
            if (i == 8) {
                System.out.print(localDoska[i]);
            } else if (i == 2 || i == 5) {
                System.out.printf("%c%n------%n", localDoska[i]);
            } else {
                System.out.print(localDoska[i] + "|");
            }
        }
    }

    public static char[] tahPocitaca(char[] tahX) {

        Random random = new Random();
        int nahodnyIndex;
        while (true) {
            nahodnyIndex = random.nextInt(0, tahX.length - 1);
            if (tahX[nahodnyIndex] != ' ') {
                System.out.printf("Index %d je uz obsadeny", nahodnyIndex + 1);
            }
            else {
                break;
            }
        }
        tahX[nahodnyIndex] = 'X';
        return tahX;
    }

    public static void vysledokHry(char[] localDoska) {
        for (int i = 0; i < localDoska.length; i++) {
            if (localDoska[i] == ' ') {
                break;
            } else if ((localDoska[0] == 'X' && localDoska[1] == 'X' && localDoska[2] == 'X') ||
                    (localDoska[3] == 'X' && localDoska[4] == 'X' && localDoska[5] == 'X') ||
                    (localDoska[6] == 'X' && localDoska[7] == 'X' && localDoska[8] == 'X') ||
                    (localDoska[0] == 'X' && localDoska[3] == 'X' && localDoska[6] == 'X') ||
                    (localDoska[1] == 'X' && localDoska[4] == 'X' && localDoska[7] == 'X') ||
                    (localDoska[2] == 'X' && localDoska[5] == 'X' && localDoska[8] == 'X') ||
                    (localDoska[0] == 'X' && localDoska[4] == 'X' && localDoska[8] == 'X') ||
                    (localDoska[2] == 'X' && localDoska[4] == 'X' && localDoska[6] == 'X')) {
                System.out.println("Pocitac vyhral");
                try {
                    Thread.sleep(4000);
                } catch (InterruptedException e) {
                    throw new RuntimeException(e);
                } finally {

                }
                ;
                System.exit(0);
            } else if ((localDoska[0] == 'O' && localDoska[1] == 'O' && localDoska[2] == 'O') ||
                    (localDoska[3] == 'O' && localDoska[4] == 'O' && localDoska[5] == 'O') ||
                    (localDoska[6] == 'O' && localDoska[7] == 'O' && localDoska[8] == 'O') ||
                    (localDoska[0] == 'O' && localDoska[3] == 'O' && localDoska[6] == 'O') ||
                    (localDoska[1] == 'O' && localDoska[4] == 'O' && localDoska[7] == 'O') ||
                    (localDoska[2] == 'O' && localDoska[5] == 'O' && localDoska[8] == 'O') ||
                    (localDoska[0] == 'O' && localDoska[4] == 'O' && localDoska[8] == 'O') ||
                    (localDoska[2] == 'O' && localDoska[4] == 'O' && localDoska[6] == 'O')) {
                System.out.println("Uzivatel vyhral");
                try {
                    Thread.sleep(4000);
                } catch (InterruptedException e) {
                    throw new RuntimeException(e);
                } finally {

                }
                ;
            } else {
                System.out.println("Vysledok hry je remiza");

            }
        }
    }
}






//vytvorit hernu dosku
// urcit pocitacu x a mne o
//vygenerovat vlozenie znaku do






import java.util.Scanner;

public class TahCloveka {
    public static char[] tahCloveka(char[] tahO){
        Scanner scanner = new Scanner(System.in);

        int index;

        while (true) {
            try {
                System.out.print("Zadaj index (1-9): ");
                index = (scanner.nextInt()) -1;

                // Kontrola, či je index v rozsahu
                if (index < 0 || index >= tahO.length) {
                    throw new IndexOutOfBoundsException("Index mimo rozsah!");
                }
                else if (tahO[index] != ' ') {
                    System.out.println("Dany index je uz plny");
                    }
                    else {tahO[index] = 'O';
                        break;
                    }
            // Ukončenie cyklu, ak je index v správnom rozsahu
            } catch (IndexOutOfBoundsException e) {
                System.out.println("Chyba: " + e.getMessage());
            } catch (Exception e) {
                System.out.println("Chyba: Zadaj platné číslo.");
                scanner.next(); // Vyčistenie neplatného vstupu
            }
        }
        scanner.close();
        return tahO;
    }
}


