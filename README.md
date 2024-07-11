# reverse-substrings-between-each-pair-of-parentheses
class Solution {
    public String reverseParentheses(String s) {
       Stack<Character> stack = new Stack<>();
        
        for (char c : s.toCharArray()) {
            if (c == ')') {
                StringBuilder sb = new StringBuilder();
                
                // Pop characters until '(' is found
                while (!stack.isEmpty() && stack.peek() != '(') {
                    sb.append(stack.pop());
                }
                
                // Remove the '('
                if (!stack.isEmpty() && stack.peek() == '(') {
                    stack.pop();
                }
                
                // Push the reversed string back onto the stack
                for (char ch : sb.toString().toCharArray()) {
                    stack.push(ch);
                }
            } else {
                stack.push(c);
            }
        }
        
        // Build the result from the stack
        StringBuilder result = new StringBuilder();
        for (char c : stack) {
            result.append(c);
        }
        
        return result.toString(); 
    }
}
