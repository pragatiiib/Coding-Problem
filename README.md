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
Cycle in a linked list
You are given a linked list 
A
A of size 
N
N.

Return the node where the cycle begins in the linked list. If there is no cycle, return NULL.

Input:
First line will contain 
T
T, number of test cases. Then the test cases follow.
Each test case contains three lines of input.
First line contains an integer 
N
N, length of the linked list 
A
A.
Second line contains 
A
1
,
A
2
,
…
A
N
A 
1
​
 ,A 
2
​
 ,…A 
N
​
 , the value of the linked list nodes starting from the head for the linked list.
Third line contains an integer denoting the index of the node where the cycle starts.
Note:

For Java language, you need to:
Complete the function in the submit solution tab:

Node detectCycle(Node head){...}
 
 

For C++ language, you need to:
Complete the function in the submit solution tab:

Node* detectCycle(Node* head){...}
 
 

For Python language, you need to:
Complete the function in the submit solution tab:

def detectCycle(head):
Output:
The function you complete should return the required answer.

Constraints
1
≤
T
≤
10
1≤T≤10
1
≤
N
≤
1
0
5
1≤N≤10 
5
 
1
≤
A
i
≤
1
0
9
1≤A 
i
​
 ≤10 
9
 
Sample Input:
3
2
8 5
1
2
5 9
1
3
5 6 8
2
Sample Output:
8
5
6
Sample Explanation:
Test case 
1
1: The list is of the form 
8
⇌
5
8⇌5, where 
8
8 is the head. Thus, the cycle starts from 
8
8.

Test case 
2
2: The list is of the form 
5
⇌
9
5⇌9, where 
5
5 is the head. Thus, the cycle starts from 
5
5.

Test case 
3
3: The list is of the form 
5
→
6
⇌
8
5→6⇌8, where 
5
5 is the head. Thus, the cycle starts from 
6
6.

Sample 1:
Input
Output
3
2
8 5
1
2
5 9
1
3
5 6 8
2
8
5
6
Q4Find Middle Element of Linked List
You are given the head of a singly linked list 
A
A of length 
N
N. The values in the list are 
A
1
,
A
2
,
…
,
A
N
A 
1
​
 ,A 
2
​
 ,…,A 
N
​
  respectively. You need to find the value of the middle element of the linked list.

The middle element of a linked list of length 
N
N is the 
(
⌊
N
2
⌋
+
1
)
(⌊ 
2
N
​
 ⌋+1)-th element from the head of the list.

Input Format
The first line of the input contains a single integer 
T
T - the number of test cases. The description of 
T
T test cases follows.

The first line of each test case contains a single integer 
N
N.

The second line of each test case contains 
N
N space-separated integers 
A
1
,
A
2
,
…
,
A
N
A 
1
​
 ,A 
2
​
 ,…,A 
N
​
 .

Output Format
For each test case, the function you complete should return the value of the middle element of the list.
Note: You need to complete the function getMiddleElement to solve the problem.

Constraints
1
≤
T
≤
100
1≤T≤100
1
≤
N
≤
1
0
5
1≤N≤10 
5
 
1
≤
A
i
≤
1
0
9
1≤A 
i
​
 ≤10 
9
  for each valid 
i
i
the sum of 
N
N over all test cases does not exceed 
2
⋅
1
0
5
2⋅10 
5
 
Sample 1:
Input
Output
3
5
1 2 3 4 5
6
1 2 3 4 5 6
4
10 1 6 12
3
4
6
Explanation:
Example case 1: The value of the middle element is 
A
3
=
3
A 
3
​
 =3.

Example case 2: The value of the middle element is 
A
4
=
4
A 
4
​
 =4.

Example case 3: The value of the middle element is 
A
3
=
6
A 
3
​
 =6.
Sample 2:
Input
Output
7
1 2 3 2 1 3 2 
3
Explanation:

//derived from aizu0121
#include <string>
#include <vector>
#include <queue>
#include <map>
#include <cstdio>
using namespace std;
int main(){
	int X,i,j,t;
	vector<int>problem;
	scanf("%d",&X);
	for(i=0;i<X*X;i++)scanf("%d",&t),problem.push_back(t);

	int Y=X;
	map<vector<int>,pair<int,int> >m;
	map<vector<int>,pair<vector<int>,string> >prev;
	queue<vector<int> >q;
	vector<int>v,next;
	for(i=0;i<X*Y;i++)v.push_back(i);
	m[v]=make_pair(0,0);
	prev[v]=make_pair(v,"");
	for(q.push(v);!q.empty();){
		v=q.front();q.pop();
		int coor=m[v].first,x=coor%X,y=coor/X;
		int depth=m[v].second;
		next=v;
		if(0<x){
			swap(v[coor],v[coor-1]);
			if(m.find(v)==m.end())m[v]=make_pair(coor-1,depth+1),q.push(v),prev[v]=make_pair(next,"RIGHT");
			swap(v[coor],v[coor-1]);
		}
		if(x<X-1){
			swap(v[coor],v[coor+1]);
			if(m.find(v)==m.end())m[v]=make_pair(coor+1,depth+1),q.push(v),prev[v]=make_pair(next,"LEFT");
			swap(v[coor],v[coor+1]);
		}
		if(0<y){
			swap(v[coor],v[coor-X]);
			if(m.find(v)==m.end())m[v]=make_pair(coor-X,depth+1),q.push(v),prev[v]=make_pair(next,"DOWN");
			swap(v[coor],v[coor-X]);
		}
		if(y<Y-1){
			swap(v[coor],v[coor+X]);
			if(m.find(v)==m.end())m[v]=make_pair(coor+X,depth+1),q.push(v),prev[v]=make_pair(next,"UP");
			swap(v[coor],v[coor+X]);
		}
		if(m.find(problem)!=m.end())break;
	}

	printf("%d\n",m[problem].second);
	for(;prev[problem].first!=problem;){
		puts(prev[problem].second.c_str());
		problem=prev[problem].first;
	}
}
code:
//derived from aizu0121
#include <string>
#include <vector>
#include <queue>
#include <map>
#include <cstdio>
using namespace std;
int main(){
    int X,i,j,t;
    vector<int>problem;
    scanf("%d",&X);
    for(i=0;i<X*X;i++)scanf("%d",&t),problem.push_back(t);

    int Y=X;
    map<vector<int>,pair<int,int> >m;
    map<vector<int>,pair<vector<int>,string> >prev;
    queue<vector<int> >q;
    vector<int>v,next;
    for(i=0;i<X*Y;i++)v.push_back(i);
    m[v]=make_pair(0,0);
    prev[v]=make_pair(v,"");
    for(q.push(v);!q.empty();){
        v=q.front();q.pop();
        int coor=m[v].first,x=coor%X,y=coor/X;
        int depth=m[v].second;
        next=v;
        if(0<x){
            swap(v[coor],v[coor-1]);
            if(m.find(v)==m.end())m[v]=make_pair(coor-1,depth+1),q.push(v),prev[v]=make_pair(next,"RIGHT");
            swap(v[coor],v[coor-1]);
        }
        if(x<X-1){
            swap(v[coor],v[coor+1]);
            if(m.find(v)==m.end())m[v]=make_pair(coor+1,depth+1),q.push(v),prev[v]=make_pair(next,"LEFT");
            swap(v[coor],v[coor+1]);
        }
        if(0<y){
            swap(v[coor],v[coor-X]);
            if(m.find(v)==m.end())m[v]=make_pair(coor-X,depth+1),q.push(v),prev[v]=make_pair(next,"DOWN");
            swap(v[coor],v[coor-X]);
        }
        if(y<Y-1){
            swap(v[coor],v[coor+X]);
            if(m.find(v)==m.end())m[v]=make_pair(coor+X,depth+1),q.push(v),prev[v]=make_pair(next,"UP");
            swap(v[coor],v[coor+X]);
        }
        if(m.find(problem)!=m.end())break;
    }

    printf("%d\n",m[problem].second);
    for(;prev[problem].first!=problem;){
        puts(prev[problem].second.c_str());
        problem=prev[problem].first;
    }
}Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

 

Example 1:

Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]
Example 2:

Input: n = 1
Output: ["()"}

 solution :import java.util.ArrayList;
import java.util.List;

public class Solution {

    public List<String> generateParenthesis(int n) {
        List<String> result = new ArrayList<>();
        backtrack(result, "", 0, 0, n);
        return result;
    }

    private void backtrack(List<String> result, String current, int open, int close, int max) {
        if (current.length() == max * 2) {
            result.add(current);
            return;
        }

        if (open < max) {
            backtrack(result, current + "(", open + 1, close, max);
        }
        if (close < open) {
            backtrack(result, current + ")", open, close + 1, max);
        }
    }

    // For local testing
    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.generateParenthesis(3));
        System.out.println(sol.generateParenthesis(1));
    }
}

 

