# Delete Anagrams

> An anagram of a word, is another word that is of the same length as the original word but with a change in the order the characters. You are given an array of Strings.&#x20;
>
> You read the array from left to right, if you read a word that is an anagram of any previous word, delete the current word. Return the array with all anagrams deleted by following the above mentioned method. Return the array in ascending alphabetical order.
>
> eg) arr = \["code" , "dcoe" , "timer", "timerr", "remit"]&#x20;
>
> answer = \["code", "timer", "timerr"]

```
public static List<String> deleteAnagrams(String[] arr) {
        Set<String> uniqueWords = new HashSet<>();
        List<String> result = new ArrayList<>();

        for (String word : arr) {
            boolean isAnagram = false;
            char[] charArray = word.toCharArray();
            Arrays.sort(charArray);
            String sortedWord = new String(charArray);

            if (!uniqueWords.contains(sortedWord)) {
                uniqueWords.add(sortedWord);
                result.add(word);
            }
        }

        return result;
    }
    
    
public static void main(String[] args) {
        String[] arr = {"code", "dcoe", "timer", "timerr", "remit"};
        List<String> result = deleteAnagrams(arr);

        for (String word : result) {
            System.out.println(word);
        }
    }
```
