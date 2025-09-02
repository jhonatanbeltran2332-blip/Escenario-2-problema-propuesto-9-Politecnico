# Escenario-2-problema-propuesto-9-Politecnico
En el repositorio se encuentra un código para java, perteneciente al problema 9 del escenario número 2, el cual permite contar cuántos números primos existen en un intervalo dado, entre dos enteros (mínimo 2 y máximo 20000). Este aporte puede ser bastante útil para proyectos que requieran validación numérica o generación de intervalos primos.
package primeinterval;

/**
 * PrimeIntervalCounter
 * --------------------
 * This program calculates how many prime numbers exist in a given interval.
 *
 * Input: two positive integers greater or equal than 2 and less or equal than 20000.
 * Output: the quantity of prime numbers within the interval.
 *
 * Example 1:
 * Input: 8 10
 * Output: 0
 *
 * Example 2:
 * Input: 10 20
 * Output: 4
 *
 * Example 3:
 * Input: 11 19
 * Output: 4
 *
 * Author: Your Name
 * Date: 2025-09-02
 */

import java.util.Scanner;

public class PrimeIntervalCounter {

    /**
     * Main method that drives the program.
     * It reads two integers from standard input and prints
     * the number of primes within the given interval.
     */
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter two integers between 2 and 20000 (inclusive):");
        int start = scanner.nextInt();
        int end = scanner.nextInt();

        // Ensure the interval is correctly ordered
        if (start > end) {
            int temp = start;
            start = end;
            end = temp;
        }

        int primeCount = countPrimesInInterval(start, end);

        System.out.println("Number of prime numbers in the interval: " + primeCount);
    }

    /**
     * Counts the number of prime numbers within the given interval.
     *
     * @param start the lower bound of the interval (inclusive)
     * @param end the upper bound of the interval (inclusive)
     * @return the number of prime numbers found
     */
    public static int countPrimesInInterval(int start, int end) {
        int count = 0;
        for (int number = start; number <= end; number++) {
            if (isPrime(number)) {
                count++;
            }
        }
        return count;
    }

    /**
     * Checks whether a given number is prime.
     *
     * @param n the number to check
     * @return true if the number is prime, false otherwise
     */
    public static boolean isPrime(int n) {
        if (n < 2) return false;
        if (n == 2) return true;
        if (n % 2 == 0) return false;

        int sqrt = (int) Math.sqrt(n);
        for (int i = 3; i <= sqrt; i += 2) {
            if (n % i == 0) {
                return false;
            }
        }
        return true;
    }
}
