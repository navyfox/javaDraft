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

        Integer number = getRowFromFile("/Users/rim/project/first2017/src/input.txt");
        System.out.println(number);


        int n = number;
        int sizeArray = n - 16;
        int[] numbers = new int[sizeArray];
        Writer wr = new FileWriter ("/Users/rim/project/first2017/src/output.txt");

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
   
