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
