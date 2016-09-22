# ssp
Small summer projects; as implied, little coding projects I've done in my free time

public class ProjectEuler {
	
	public static int multiples3and5(int max) {
		int sum = 0;
		for (int i = 0; i < max; i++) {
			if (i % 3 == 0 || i % 5 == 0) {
				sum += i;
			}
		}
		return sum;
	}
	
	public static int largestPrime(int max) {
		int largestPrime = 0;
		boolean prime = true;
		for (int i = 1; i < max; i++) {
			prime = true;
			for (int j = 1; j <= i; j++) {
				if (i % j == 0 && (j != 1 && j != i)) {
					prime = false;
				}
			}
			if (prime == true) {
				if (max % i == 0) {
					largestPrime = i;
				}
			}
			if (largestPrime == 1) {
				largestPrime = max;
			}
		}
		return largestPrime;
	}
	
	public static boolean palindrome(String input) {
		if (input == null || input.length() <= 1) {
			return true;
		}
		char first = input.charAt(0);
		char last = input.charAt(input.length() - 1);
		if (first != last) {
			return false;
		}
		String middle = input.substring(1, input.length() - 1);
		return palindrome(middle);
	}
	
	public static String converter(int baseTen, int base) {
		int temp = 0;
		String result = "";
		do {
			temp = baseTen % base;
			result = temp + result;
			baseTen /= base;
		} while (baseTen != 0);
		return result;
	}
	
	public static void doubleBasePalindromes(int max) {
		String iString;
		String iString2;
		for (int i = 0; i < max; i++) {
			iString = "" + i;
			if (palindrome(iString)) {
				iString2 = converter(Integer.parseInt(iString), 2);
				if (palindrome(iString2)) {
					System.out.println(i);
				}
			}
		}
	}
	
	public static void multiplicationTable(int max) {
		for (int i = 1; i <= max; i++) {
			for (int j = 1; j <= max; j++) {
				System.out.printf("%2d ", j * i);
			}
			System.out.println();
		}
	}
	
	public static void main(String[] args) {
		System.out.println(multiples3and5(86));
		System.out.println(largestPrime(24));
		doubleBasePalindromes(100);
		multiplicationTable(5);
	}
	
}
