# javaDraft
   
## First

    /**
    * IntelliJ IDEA 2017.1.1
    * Build #IC-171.4073.35, built on April 7, 2017
    * JRE: 1.8.0_112-release-736-b16 x86_64
    * JVM: OpenJDK 64-Bit Server VM by JetBrains s.r.o
    * JDK: 1.8.0_121
    * Created by rim on 07.05.17.
    */

    import java.io.File;
    import java.io.FileNotFoundException;
    import java.io.FileWriter;
    import java.io.Writer;
    import java.util.Scanner;

    public class Main {

    private static final int MIN = 16;
    private static final String INPUT_FILE_NAME = "input.txt";
    private static final String OUTPUT_FILE_NAME = "output.txt";

    public static void main(String[] args) throws Exception {

        int max = getIntFromFile(INPUT_FILE_NAME);

        Writer outputFile = new FileWriter (OUTPUT_FILE_NAME);

        for (int i = MIN; i < max; i++) {
            outputFile.write(Integer.toHexString(i) + "\n");
        }

        outputFile.close();
    }

    private static Integer getIntFromFile(String fileName) throws FileNotFoundException {
        Scanner scanner = new Scanner(new File(fileName));
        int number = scanner.nextInt();
        scanner.close();
        return number;
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
     
     
     
 ## Three
     import java.io.*;
     import java.util.ArrayList;
     import java.util.Scanner;
     import java.util.HashSet;
     public class Main {

     public static void main(String[] args) throws Exception {

        File inputFile = new File("input.txt");
        File outputFile = new File("output.txt");

        int[][] array = getArrayFromFile(inputFile.getAbsolutePath());
        ArrayList<HashSet<Integer>> arrayList = new ArrayList<>();

        for (int[] element: array) {
            HashSet<Integer> myHashSet = new HashSet<>();
            for (int i: element) {
                myHashSet.add(i);
            }
            arrayList.add(myHashSet);
        }

        ArrayList<Integer> differentLineNumbers = new ArrayList<>();

        for (int i = 0; i < arrayList.size(); i++) {

            boolean seachFlag = false;

            for (int element: differentLineNumbers) {
                HashSet<Integer> myHashSetOne = arrayList.get(i);
                HashSet<Integer> myHashSetTwo = arrayList.get(element);

                if (myHashSetOne.equals(myHashSetTwo)) {
                    seachFlag = true;
                }
            }

            if (!seachFlag) {
                differentLineNumbers.add(i);
            }

        }

        Writer wr = new FileWriter (outputFile.getAbsolutePath());

        for (int index: differentLineNumbers){
            for (int element: array[index]) {
                wr.write(element);
                System.out.println(element);
            }
            wr.write("\n");
        }
        wr.close();

     }

     private static int[][] getArrayFromFile(String fileName) throws FileNotFoundException {
        Scanner scanner = new Scanner(new File(fileName));

        int n = scanner.nextInt();
        int m = scanner.nextInt();

        int[][] array = new int[n][m];

        for(int j = 0; j < n; j++) {
            for(int i = 0; i < m; i++) {
                array[j][i] = scanner.nextInt();
            }
        }

        scanner.close();
        return array;
     }

     }
          
