package org.example;

import java.lang.reflect.Array;
import java.util.Scanner;
import static java.lang.System.*;

public class Main {

    public static void main(String[] args) throws Exception {

        out.println("Добро пожаловать в консольное приложение “Калькулятор”!");
        out.println("Введите строку с арифметическим выражением операций (+, -, * или /) между двумя целыми числами от 1 до 10 через пробелы:");

        Scanner sc = new Scanner(in);

        String str = sc.nextLine();

        out.println(calc(str));

    }

    public static String calc(String input) throws Exception {

        String[] arr = input.split(" ");
        int length = Array.getLength(arr);

        if (length != 3) {
            if (length < 3) {
                throw new Exception("т.к. строка не является математической операцией");
            } else {
                throw new Exception("т.к. формат математической операции не удовлетворяет заданию - два операнда и один оператор (+, -, /, *)");
            }
        }

        byte a = Byte.parseByte(arr[0]);
        byte b = Byte.parseByte(arr[2]);
        String operation = String.valueOf(arr[1]);
        byte result;

        if (a < 1 || a > 10 || b < 1 || b > 10) throw new Exception("введите число от 1 до 10");

        result = switch (operation) {
            case "+" -> (byte) (a + b);
            case "-" -> (byte) (a - b);
            case "*" -> (byte) (a * b);
            case "/" -> (byte) (a / b);
            default -> throw new Exception();
        };

        return String.valueOf(result);
    }
}
