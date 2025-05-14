# Coding-Problem
interview bit 
q1. Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.


 

Example 1:

Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
Example 2:

Input: digits = ""
Output: []
Example 3:

Input: digits = "2"
Output: ["a","b","c"]
 

Constraints:

0 <= digits.length <= 4
digits[i] is a digit in the range ['2', '9'].
solution:
import java.util.ArrayList;
import java.util.List;

class Solution {
    private static final String[] LETTERS = {
        "",     // 0
        "",     // 1
        "abc",  // 2
        "def",  // 3
        "ghi",  // 4
        "jkl",  // 5
        "mno",  // 6
        "pqrs", // 7
        "tuv",  // 8
        "wxyz"  // 9
    };
    
    public List<String> letterCombinations(String digits) {
        List<String> result = new ArrayList<>();
        if (digits == null || digits.length() == 0) {
            return result;
        }
        backtrack(result, new StringBuilder(), digits, 0);
        return result;
    }
    
    private void backtrack(List<String> result, StringBuilder current, String digits, int index) {
        if (index == digits.length()) {
            result.add(current.toString());
            return;
        }
        
        char digit = digits.charAt(index);
        String letters = LETTERS[digit - '0'];
        
        for (int i = 0; i < letters.length(); i++) {
            current.append(letters.charAt(i));
            backtrack(result, current,digits, index + 1);
            current.deleteCharAt(current.length() - 1);
        }
    }
}
q2Given the head of a linked list, remove the nth node from the end of the list and return its head.

 

Example 1:


Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
Example 2:

Input: head = [1], n = 1
Output: []
Example 3:

Input: head = [1,2], n = 1
Output: [1]
 

Constraints:

The number of nodes in the list is sz.
1 <= sz <= 30
0 <= Node.val <= 100
1 <= n <= sz
solution :
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        
        ListNode fast = dummy;
        ListNode slow = dummy;
        
        // Move fast n+1 steps ahead
        for (int i = 0; i <= n; i++) {
            fast = fast.next;
        }
        
        // Move both pointers until fast reaches end
        while (fast != null) {
            fast = fast.next;
            slow = slow.next;
        }
        
        // Remove the nth node from end
        slow.next = slow.next.next;
        
        return dummy.next;
    }
}
difficult didnt solve
String Operations
Python
Strings
easy
74.5% Success

12

1

Bookmark
Strings are bits of text. We can define that using single or double quotes.

We can do many operations on string as described below.

my_string = "Hello InterviewBit"
print(len(my_string)) #prints 18
Finds length of string using built-in len() method.

my_string = "Hello InterviewBit"
print(my_string.index("l"))
# prints 2
Finds the first index of character ‘l’. Notice how there are actually two l’s in the phrase - this method only recognizes the first.

my_string = "Hello InterviewBit"
print(my_string.count("e"))
This counts the number of e’s in the string. Therefore, it should print 3.

my_string = "Hello InterviewBit"
print(my_string[2:7])
# prints "llo I"
This prints a slice of the string, starting at index 2, and ending at index 6.

my_string = "Hello InterviewBit"
print(my_string[2:7:2])
# prints "loI"
This prints the characters of string from 2 to 7 skipping one character. This is extended slice syntax. The general form is [start:stop:step].

my_string = "Hello InterviewBit"
print(my_string.upper())
print(my_string.lower())
These make a new string with all letters converted to uppercase and lowercase, respectively.

Try the following example in the editor below.

Given a string S and you have to do certain operations as described in the comments below.


codecHEF DIFFICULTY QUE
Critical points in a Linked List
Given the head of a linked list, Find the number of critical points. (The starting and end are not considered critical points).

Local minima or maxima are called critical points.

A Node is called a local minima if both next and previous elements are greater than the current element.

A Node is called a local maxima if both next and previous elements are smaller than the current element.

Constraints
1
≤
1≤ Number of elements in the linked list , 
N
N 
≤
1
0
5
≤10 
5
 
1
≤
N
o
d
e
.
d
a
t
a
≤
1
0
9
1≤Node.data≤10 
9
 
Sample 1:
Input
Output
8
1 2 3 3 3 5 1 3
2 
Explanation:
1 is a minima and 5 is a maxima hence there are 2 critical points

Sample 2:
Input
Output
7
1 2 3 2 1 3 2 
3
Explanation:
