```java
public class TrieNode
{
    private char c;
    public boolean isWord;
    private TrieNode node;
    public TrieNode[] children = new TrieNode[26];
    public TrieNode() {};
    public TrieNode(char c)
    {
        this.node = new TrieNode();
        this.c = c;
    }
}

class Trie {
    private TrieNode root;

    /** Initialize your data structure here. */
    public Trie() {
        root = new TrieNode(' ');
    }

    /** Inserts a word into the trie. */
    public void insert(String word) {
        TrieNode tn = root;
        for (int i = 0; i < word.length(); i++)
        {
            char c = word.charAt(i);
            if (tn.children[c - 'a'] == null) tn.children[c - 'a'] = new TrieNode(c);
            tn = tn.children[c - 'a'];
        }
        tn.isWord = true;
    }

    /** Returns if the word is in the trie. */
    public boolean search(String word) {
        TrieNode tn = root;
        for (int i = 0; i < word.length(); i++)
        {
            char c = word.charAt(i);
            if (tn.children[c - 'a'] == null) return false;
            tn = tn.children[c - 'a'];
        }
        return tn.isWord;
    }

    /** Returns if there is any word in the trie that starts with the given prefix. */
    public boolean startsWith(String prefix) {
        TrieNode tn = root;
        for (int i = 0; i < prefix.length(); i++)
        {
            char c = prefix.charAt(i);
            if (tn.children[c - 'a'] == null) return false;
            tn = tn.children[c - 'a'];
        }
        return true;
    }
}
```
