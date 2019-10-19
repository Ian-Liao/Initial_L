This is a useful method when you need to swap two characters in a String in java. Especially for the String category problems.

```java
class Solution {
    private String swap(String str, int i, int j) {
        StringBuilder sb = new StringBuilder(str);
        sb.setCharAt(i, str.charAt(j));
        sb.setCharAt(j, str.charAt(i));
        return sb.toString();
    }
}
```
