# Return_The_Start_Index_Length_Give_Substrong_Max_Index_Length


package com.nt.important.java8;

import java.util.Comparator;

import java.util.stream.Stream;

/**
 * 
 * Return the start index and length of the longest substring having identical
 * 
 * characters in a given String. i/p:S="aabbbbbccddb"
 * 
 * o/p: [2,5] using java 8 stream api and java code.
 * 
 * @author Firoj
 * 
 * @since 2022-01-05
 */
public class LongestSubString {

//	public static int[] findLongestIdenticalSubstring(String s) {

//		int[] result = new int[2];

//		int maxLength = 1;

//		int start = 0;
//
//		for (int i = 1; i < s.length(); i++) {

//			if (s.charAt(i) == s.charAt(i - 1)) {

//				maxLength++;

//			} else {

//				if (maxLength > result[1]) {

//					result[0] = start;

//					result[1] = maxLength;

//				}

//				maxLength = 1;

//				start = i;

//			}

//		}
//
//		if (maxLength > result[1]) {

//			result[0] = start;

//			result[1] = maxLength;

//		}
//
//		return result;

//	}
//
//	public static void main(String[] args) {

//		String s = "aabbbbbccddb";

//		int[] result = findLongestIdenticalSubstring(s);

//		System.out.println(result[0] + ", " + result[1]);

//	}

	/**
	 * the string and find the longest substring having identical characters. The
  
	 * code first initializes a int[] array to store the start index and length of
  
	 * the longest substring. Then, it iterates through the string, starting at
  
	 * index 1. If the current character is the same as the previous character, the
  
	 * code increments the maxLength variable. Otherwise, the code checks if the
  
	 * current maxLength value is greater than the value stored in the result array.
  
	 * If it is, the code updates the result array with the current start and
  
	 * maxLength values. Finally, the code returns the result array.
  
	 * 
	 */
	
	
	public static int[] findLongestIdenticalSubstring(String s) {
 
		return Stream.iterate(0, i -> i + 1).takeWhile(i -> i < s.length()).map(i -> {
  
			String substring = s.substring(i, i + 1);
   
			int length = 1;
   
			while (i + length < s.length() && s.charAt(i + length) == substring.charAt(0)) {
   
				length++;
    
			}
   
			return new int[] { i, length };
   
		}).max(Comparator.comparingInt(a -> a[1])).orElse(new int[0]);
  
	}

	public static void main(String[] args) {
 
		String s = "aabbbbbccddb";
  
		int[] result = findLongestIdenticalSubstring(s);
  
		System.out.println("[" + result[0] + ", " + result[1] + "]");
  
	}
 
}

/**
 * the iterate() method to create an infinite stream of integers starting from
 * 
 * 0. The takeWhile() method then takes the first s.length() elements from the
   1. 
 * stream. The map() method then maps each element in the stream to a new int[]
 * 
 * array, where the first element is the index of the substring and the second
 * 
 * element is the length of the substring. The max() method then finds the
 * 
 * element in the stream with the maximum length. Finally, the orElse() method
 * 
 * returns the default value if the stream is empty.
 * 
 * To run this code, you can save it as a Java file and compile it with the
 * 
 * following command:
 * 
 * javac LongestIdenticalSubstring.java Then, you can run the code with the
 * 
 * following command:
 * 
 * java LongestIdenticalSubstring This will print the start index and length of
 * 
 * the longest substring having identical characters in the string s. For the
 * 
 * input string "aabbbbbccddb", the output will be [2, 5].
 * 
 * Enter a prompt here
 */
