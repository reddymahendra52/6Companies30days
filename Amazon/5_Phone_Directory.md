# 5. Phone Directory
## GFG(Geeks For Geeks)
### Prompt:
Given a list of contacts **contact[]** of length **n** where each contact is a string which exist in a phone directory and a query string **str**. 
The task is to implement a search query for the phone directory. Run a search query for each prefix **p** of the query string **str** (i.e. from  index 1 to |s|) that 
prints all the distinct contacts which have the same prefix as p in **lexicographical increasing order**. 
**Note:** If there is no match between query and contacts, print "0".

```java
class Solution{
    static ArrayList<ArrayList<String>> displayContacts(int n, 
                                        String contact[], String str)
    {
        // code here
        HashSet<String> set = new HashSet<>();
       for (String ele : contact) {
           set.add(ele);
       }
       contact = new String[set.size()];
       int j = 0;
       for (String ele : set) {
           contact[j++] = ele;
       }
       Arrays.sort(contact);
       ArrayList<ArrayList<String>> result = new ArrayList<>();
       for (int i = 0; i < str.length(); i++) {
           result.add(new ArrayList<>());
       }
       
       for (String cont : contact) {
           for (int i = 0; i < cont.length(); i++) {
               if (i < str.length() && str.charAt(i) == cont.charAt(i)) {
                   result.get(i).add(cont);
               } else {
                   break;
               }
           }
       }
       
       for (int i = 0; i < str.length(); i++) {
           if (result.get(i).size() == 0) {
               result.get(i).add("0");
           }
       }
       
       return result;
    }
}

```
