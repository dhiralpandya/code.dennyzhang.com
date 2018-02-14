# Leetcode: Shortest Word Distance II     :BLOG:Medium:


---

Shortest Word Distance II  

---

Similar Problems:  
-   [Shortest Word Distance](https://brain.dennyzhang.com/shortest-word-distance)
-   Tag: [#linkedlist](https://brain.dennyzhang.com/tag/linkedlist)

---

This is a follow up of [Shortest Word Distance](https://brain.dennyzhang.com/shortest-word-distance). The only difference is now you are given the list of words and your method will be called repeatedly many times with different parameters. How would you optimize it?  

Design a class which receives a list of words in the constructor, and implements a method that takes two words word1 and word2 and return the shortest distance between these two words in the list.  

For example,  
Assume that words = ["practice", "makes", "perfect", "coding", "makes"].  

Given word1 = "coding", word2 = "practice", return 3.  
Given word1 = "makes", word2 = "coding", return 1.  

Note:  
You may assume that word1 does not equal to word2, and word1 and word2 are both in the list.  

Github: [challenges-leetcode-interesting](https://github.com/DennyZhang/challenges-leetcode-interesting/tree/master/shortest-word-distance-ii)  

Credits To: [leetcode.com](https://leetcode.com/problems/shortest-word-distance-ii/description/)  

Leave me comments, if you have better ways to solve.  

    ## Blog link: https://brain.dennyzhang.com/shortest-word-distance-ii
    ## Basic Ideas: Use hashmap to save two string comparision
    ##
    ## Complexity: Time O(n), Space O(n)
    import sys
    class WordDistance(object):
    
        def __init__(self, words):
            """
            :type words: List[str]
            """
            self.d = {}
            self.words = words
            counter = 0
            for word in words:
                if word not in self.d:
                    self.d[word], counter = counter, counter + 1
    
        def shortest(self, word1, word2):
            """
            :type word1: str
            :type word2: str
            :rtype: int
            """
            p1, p2, res = -1, -1, sys.maxsize
            for i in range(len(self.words)):
                word = self.words[i]
                if self.d[word] in [self.d[word1], self.d[word2]]:
                    if self.d[word] == self.d[word1]:
                        p1 = i
                    else:
                        p2 = i
                    if p1 != -1 and p2 != -1:
                        res = min(res, abs(p1-p2))
            return res
    
    # Your WordDistance object will be instantiated and called as such:
    # obj = WordDistance(words)
    # param_1 = obj.shortest(word1,word2)