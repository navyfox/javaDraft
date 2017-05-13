# javaDraft
   
## First

    /**
    * IntelliJ IDEA 2017.1.1
    * Build #IC-171.4073.35, built on April 7, 2017
    * JRE: 1.8.0_112-release-736-b16 x86_64
    * JVM: OpenJDK 64-Bit Server VM by JetBrains s.r.o
    * JDK: 1.8.0_121
    * Created by rim on 13.05.17.
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
     /**
     * IntelliJ IDEA 2017.1.1
     * Build #IC-171.4073.35, built on April 7, 2017
     * JRE: 1.8.0_112-release-736-b16 x86_64
     * JVM: OpenJDK 64-Bit Server VM by JetBrains s.r.o
     * JDK: 1.8.0_121
     * Created by rim on 13.05.17.
     */
     import java.io.File;
     import java.io.FileWriter;
     import java.io.IOException;
     import java.io.Writer;
     import java.util.Scanner;

     public class Main {
     private static final String ESCAPE_SPACES_REGEX = "\\s+";
     private static final String EMPTY_RESULT = "отсутствует";
     private static final String INPUT_FILE_NAME = "input.txt";
     private static final String OUTPUT_FILE_NAME = "output.txt";

     public static void main(String[] args) throws IOException {

        Scanner scanner = new Scanner(new File(INPUT_FILE_NAME));

        String[] wordsArrayOne = scanner.nextLine().split(ESCAPE_SPACES_REGEX);
        String[] wordsArrayTwo = scanner.nextLine().split(ESCAPE_SPACES_REGEX);

        scanner.close();

        String longestMatch = getStringEqualElements(wordsArrayOne, wordsArrayTwo);

        if (longestMatch == null) {
            longestMatch = EMPTY_RESULT;
        }

        Writer outputFile = new FileWriter (OUTPUT_FILE_NAME);
        outputFile.write(longestMatch);
        outputFile.close();
     }

     private static String getStringEqualElements(final String[] arrayOne, final String[] arrayTwo) {
        String tempResult = null;
        for (String elementOne: arrayOne) {
            for (String elementTwo: arrayTwo) {
                if (elementOne.equals(elementTwo) && (tempResult == null || elementOne.length() > tempResult.length())) {
                    tempResult = elementOne;
                }
            }
        }
        return tempResult;
     }


     }
     
     
     
 ## Three
     /**
     * IntelliJ IDEA 2017.1.1
     * Build #IC-171.4073.35, built on April 7, 2017
     * JRE: 1.8.0_112-release-736-b16 x86_64
     * JVM: OpenJDK 64-Bit Server VM by JetBrains s.r.o
     * JDK: 1.8.0_121
     * Created by rim on 13.05.17.
     */
     import java.io.File;
     import java.io.FileNotFoundException;
     import java.io.FileWriter;
     import java.io.Writer;
     import java.util.HashMap;
     import java.util.HashSet;
     import java.util.Map;
     import java.util.Scanner;
     import java.util.Set;

     public class Main {

     private static final String INPUT_FILE_NAME = "input.txt";
     private static final String OUTPUT_FILE_NAME = "output.txt";

     public static void main(String[] args) throws Exception {

        Map<Set<Integer>, int[]> mapDifferentString = getArrayFromFile(INPUT_FILE_NAME);

        Writer outputFile = new FileWriter(OUTPUT_FILE_NAME);

        for (Map.Entry<Set<Integer>, int[]> entry : mapDifferentString.entrySet()){
            for (int element: entry.getValue()) {
                outputFile.write(element + " ");
            }
            outputFile.write("\n");
        }
        outputFile.close();

     }

     private static Map<Set<Integer>, int[]> getArrayFromFile(String fileName) throws FileNotFoundException {
        Scanner scanner = new Scanner(new File(fileName));

        int n = scanner.nextInt();
        int m = scanner.nextInt();

        Map<Set<Integer>, int[]> map = new HashMap<>();

        for(int i = 0; i < n; i++) {
            Set<Integer> set = new HashSet<>();
            int[] array = new int[m];
            for(int j = 0; j < m; j++) {
                array[j] = scanner.nextInt();
                set.add(array[j]);
            }
            map.putIfAbsent(set, array);
        }
        scanner.close();
        return map;
     }

     }
          
