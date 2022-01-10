# 7. First non-repeating character in a stream
## GFG(Geeks For Geeks)
### Prompt:
Given an input stream of **A** of **n** characters consisting only of lower case alphabets. The task is to find the first non repeating character, each time a character is inserted to the stream. If there is no such character then append '#' to the answer.

```java
class Solution
{
    public String FirstNonRepeating(String stream)
    {
        // code here
        StringBuilder ret = new StringBuilder();
		int isRepeated[] = new int[26];
		Deque<Character> queue = new ArrayDeque<>();
		for (int i = 0; i < stream.length(); i++) {
			char ch = stream.charAt(i);
			if (isRepeated[ch - 'a'] == 0)
				queue.add(ch);
			
			isRepeated[ch - 'a']++;
			while (!queue.isEmpty() && isRepeated[queue.peek() - 'a'] != 1)
				queue.poll();
			ret.append(queue.isEmpty() ? '#' : queue.peek());

		}
		return  ret.toString();
    }
}

```
