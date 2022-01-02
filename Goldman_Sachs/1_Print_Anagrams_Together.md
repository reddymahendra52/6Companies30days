# 1. Print Anagrams Together(GFG) / Group Anagrams(Leetcode - 49 )
### Prompt
Given an array of strings, return all groups of strings that are anagrams. The groups must be created in order of their appearance in the original array.

```java

class Solution {
    public List<List<String>> Anagrams(String[] string_list) {
         Map<String, List<String> > anagrams = new HashMap<String, List<String>>();
        
        for(String word : string_list){
            char[] charArray = word.toCharArray();
            Arrays.sort(charArray);
            String sortedWord = new String(charArray);
            
            if(anagrams.containsKey(sortedWord)){
                anagrams.get(sortedWord).add(word);
            }else{
                anagrams.put(sortedWord, new ArrayList<String>(Arrays.asList(word)) );
            }
            
            
        }
        
        return new ArrayList<>(anagrams.values());
    }
}

```
