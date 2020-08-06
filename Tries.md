https://leetcode.com/explore/challenge/card/august-leetcoding-challenge/549/week-1-august-1st-august-7th/3413/

Tries is a data structure very good for dealing with retrival of a key in a dataset of strings
It's applications includes autocomplete, spellchecker, dictionary look up, etc. 
Since it's still a tree structure (N-ary tree), we can use DFS to traverse it for look up
```python
class WordDictionary:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.trie = {} 
    

    def addWord(self, word: str) -> None:
        """
        Adds a word into the data structure.
        """
        t = self.trie 
        for w in word: 
            if w not in t: 
                t[w] = {} 
            t = t[w]
        t["#"] = ""
        

    def search(self, word: str) -> bool:
        """
        Returns if the word is in the data structure. A word could contain the dot character '.' to represent any one letter.
        """
        t = self.trie 
        self.res = False
        self.dfs(t, word) 
        return self.res
    
    def dfs(self, t, word): 
        if len(word) == 0: 
            if "#" in t: 
                self.res = True
            return 
        if word[0] == '.': 
            for c in t: 
                self.dfs(t[c], word[1:]) 
        else: 
            if word[0] not in t: 
                return 
            self.dfs(t[word[0]], word[1:])
     


# Your WordDictionary object will be instantiated and called as such:
# obj = WordDictionary()
# obj.addWord(word)
# param_2 = obj.search(word)
```
