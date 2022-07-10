import java.util.Objects;
import java.util.Scanner;
import java.util.*;


class calc {
    public static void main(String[] args)  {


         Scanner scanner = new Scanner(System.in);
         String s = "";
         s = scanner.nextLine();
         System.out.println(Main.calc(s));


    }

}
class Main{
    private static final String[] LocalClassRomanNumeralsVarArrStr  = {"I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX", "X"};
    private static final String[] LocalClassArithmeticOperationsVarArrStr  = {"+", "-", "/", "*"};

    public static String calc(String input) {

        ArrayList<String> LocalOperationsVarArrStrCalc = new ArrayList();
        LocalOperationsVarArrStrCalc = FindArithmeticOperations(input);

        // 1-я проверка на ошибку, так как выдаем ошибку бессмысленно выполнять дальнейшие операции
        if (LocalOperationsVarArrStrCalc.size() == 0) {

            // Выдаём ошибку так как операндов не обнаружено
            return MуException("Операндов не обнаружено");

        }else if(LocalOperationsVarArrStrCalc.size() > 1){

            // Выдаём ошибку так как операндов больше 1

            return MуException("формат математической операции не удовлетворяет заданию - два операнда и один оператор"+LocalOperationsVarArrStrCalc);

        }

       // Fix Exception in thread
        ArrayList<String> LocalIntegerVarStr = new ArrayList();

        if(LocalOperationsVarArrStrCalc.get(0)=="+"){

            LocalIntegerVarStr = new ArrayList(Arrays.asList(input.split("\\+"))); //Dangling meta character '+' near index 0

        }else if(LocalOperationsVarArrStrCalc.get(0)=="-"){

            LocalIntegerVarStr = new ArrayList(Arrays.asList(input.split("-")));

        }else if(LocalOperationsVarArrStrCalc.get(0)=="*"){

            LocalIntegerVarStr = new ArrayList(Arrays.asList(input.split("\\*"))); // Dangling meta character '*' near index 0

        }else{

            LocalIntegerVarStr = new ArrayList(Arrays.asList(input.split("/")));

        }

        if (LocalIntegerVarStr.size() <= 1) {

            // Выдаём ошибку так как операндов не обнаружено

            return MуException("строка не является математической операцией");

        }

        //System.out.println(LocalIntegerVarStr);

        //Operator string to char
        char LocalStringToChar = LocalOperationsVarArrStrCalc.get(0).charAt(0);
         //Проверка на разные системы счисления
        if(isRoman(LocalIntegerVarStr.get(0)) && isRoman(LocalIntegerVarStr.get(1))){

            //Римский счёт счисления
            int LocalCalc = Calculated(RomanToNumber(LocalIntegerVarStr.get(0)), RomanToNumber(LocalIntegerVarStr.get(1)), LocalStringToChar);
            if (LocalCalc < 1){

                return MуException("калькулятора с римскими числами могут быть только положительные числа");

            }else {
                return IntegerToRoman(LocalCalc);
            }



            // Проверяем, что одно из чисел не является
        }else if(!isRoman(LocalIntegerVarStr.get(0)) && isRoman(LocalIntegerVarStr.get(1)) || isRoman(LocalIntegerVarStr.get(0)) && !isRoman(LocalIntegerVarStr.get(1))){

            //Выдаём ошибку так как используются одновременно разные системы счисления
            return MуException("используются одновременно разные системы счисления");


        }else{

            //Проверяем, что входные числа не превышают 10
            if(Integer.parseInt(LocalIntegerVarStr.get(0)) <= 10 && Integer.parseInt(LocalIntegerVarStr.get(1)) <= 10) {

                //Арабская система счисления
                return Integer.toString(Calculated(Integer.parseInt(LocalIntegerVarStr.get(0)), Integer.parseInt(LocalIntegerVarStr.get(1)), LocalStringToChar));

            }else{

                //Выдаём ошибку так как одно из чисел больше 10

                return MуException("калькулятор Может принимать на вход числа от 1 до 10 включительно, не более");

            }

        }


    }


    private static int Calculated (int num1, int num2, char op) {
        int result = 0;
        switch (op) {
            case '+':
                result = num1 + num2;
                break;
            case '-':
                result = num1 - num2;
                break;
            case '*':
                result = num1 * num2;
                break;
            case '/':


            try {
                result = num1 / num2;

            } catch (ArithmeticException e) {
                System.out.println("Throws Exception деление на 0"+e.getMessage());
                System.exit(0);
            }
                break;

        }
        return result;
    }
    private static boolean isRoman(String LocalVarStrFunc) {


        for (int integerOne = 0; integerOne < LocalClassRomanNumeralsVarArrStr.length; integerOne++){

            if(LocalVarStrFunc.equals(LocalClassRomanNumeralsVarArrStr[integerOne])){

                return true;

            }

        }
        return false;

    }

    private static ArrayList<String> FindArithmeticOperations(String LocalVarStrFunc){


        ArrayList<String> LocalOperationsVarArrStr = new ArrayList();

        for (int integerOne = 0; integerOne < LocalVarStrFunc.length(); integerOne++){

            //System.out.print(Character.toString(s.charAt(integerOne)));

            for (int integerTwo = 0; integerTwo < LocalClassArithmeticOperationsVarArrStr.length; integerTwo++) {

                if (Objects.equals(Character.toString(LocalVarStrFunc.charAt(integerOne)), LocalClassArithmeticOperationsVarArrStr[integerTwo])) {

                    //dump LocalOperationsVarArrStr[integerTwo] = LocalArithmeticOperationsVarArrStr[integerTwo];
                    LocalOperationsVarArrStr.add(LocalClassArithmeticOperationsVarArrStr[integerTwo]);

                }

            }

        }
        //System.out.print(LocalOperationsVarArrStr.size());
        return LocalOperationsVarArrStr;
    }
    private static int RomanToNumber(String LocalVarStrFunc){

        for (int integerOne = 0; integerOne < LocalClassRomanNumeralsVarArrStr.length; integerOne++){

            if(LocalVarStrFunc.equals(LocalClassRomanNumeralsVarArrStr[integerOne])){

                return integerOne + 1;

            }

        }
        return 0;
    }
    private static String IntegerToRoman(int LocalVarIntFunc) {

        String[] LocalRomanLiterals = {"X","IX","V","IV","I"};
        int[] LocalVarIntValues = {10,9,5,4,1};
        StringBuilder Roman = new StringBuilder();

        for(int integerOne=0; integerOne<LocalVarIntValues.length; integerOne++) {

            while(LocalVarIntFunc >= LocalVarIntValues[integerOne]) {

                LocalVarIntFunc -= LocalVarIntValues[integerOne];
                Roman.append(LocalRomanLiterals[integerOne]);

            }

        }
        return Roman.toString();
    }
    private static String MуException(String LocalException){
        try {
            throw new ArithmeticException(LocalException);

        } catch (ArithmeticException e) {
            System.out.println("Throws Exception "+e.getMessage());
            System.exit(0);
            return "Throws Exception "+e.getMessage();
        }
    }

}
