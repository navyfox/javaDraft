# javaDraft

## First
    public class Main {

    public static void main(String[] args) throws Exception {
        int n = 32;
        int sizeArray = n - 16;
    //        List<Integer> numbers = new ArrayList<>();
        int[] numbers = new int[sizeArray];

        for (int i = 0; i < sizeArray;){
            for (int m = 16; m < n; m++) {
    //                numbers.add(m);
                numbers[i] = m;
                String convert = Integer.toHexString(numbers[i]);
                System.out.println(convert);
                i++;
            }
        }


    }

    }
   
## First

    import java.util.Scanner;
    import java.io.*;
    public class Main {
    
    public static void main(String[] args) throws Exception {

        File inputFile = new File("input.txt");
        File outputFile = new File("output.txt");
        Integer number = getRowFromFile(inputFile.getAbsolutePath());
        System.out.println(number);


        int n = number;
        int sizeArray = n - 16;
        int[] numbers = new int[sizeArray];
        Writer wr = new FileWriter (outputFile.getAbsolutePath());

        for (int i = 0; i < sizeArray;){
            for (int m = 16; m < n; m++) {
                numbers[i] = m;
                String convert = Integer.toHexString(numbers[i]);
                wr.write(convert);
                wr.write("\n");
                System.out.println(convert);
                i++;
            }
        }
        wr.close();


    }

    private static Integer getRowFromFile(String fileName) throws FileNotFoundException {
        Scanner scanner = new Scanner((new File(fileName)));
        int nums = scanner.nextInt();
        scanner.close();
        return nums;
    }

    }
   
 ## Two
     import java.io.*;
     import java.util.ArrayList;
     import java.util.List;
     import java.util.Scanner;
     public class Main {

     public static void main(String[] args) throws Exception {

        File inputFile = new File("input.txt");
        File outputFile = new File("output.txt");

        Scanner scanner = new Scanner(inputFile.getAbsoluteFile());
        String textOne = scanner.nextLine();
        String textTwo = scanner.nextLine();
        scanner.close();

        String[] wordsArrayOne = textOne.split("\\s+");
        String[] wordsArrayTwo = textTwo.split("\\s+");

        String[] wordsArrayEqualElements = getStringEqualElements(wordsArrayOne, wordsArrayTwo);

        if (wordsArrayEqualElements.length == 0) {
            System.out.println("отсутствует");
        } if (wordsArrayEqualElements.length == 1) {
            System.out.println(wordsArrayEqualElements[0]);
        }

        int maxLengthString = 0;
        String stringMaxLength = "";

        for (String element: wordsArrayEqualElements){
            if (element.length() > maxLengthString) {
                maxLengthString = element.length();
                stringMaxLength = element;
            }
        }

        Writer wr = new FileWriter (outputFile.getAbsolutePath());
        wr.write(stringMaxLength);
        wr.close();
        System.out.println(stringMaxLength);

     }

     private static String[] getStringEqualElements(String[] arrayOne, String[] arrayTwo) {
        List<String> equalsArray = new ArrayList<>();
        for (String elementOne: arrayOne) {
            for (String elementTwo: arrayTwo) {
                if (elementOne.equals(elementTwo)) {
                    equalsArray.add(elementOne);
                }
            }
        }
        return equalsArray.toArray(new String[equalsArray.size()]);
     }


     }
