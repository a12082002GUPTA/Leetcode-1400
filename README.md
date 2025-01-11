# Leetcode-1400
# C++

class Solution {
public:
    bool canConstruct(string s, int k) {
        if(s.length()<k)return false;
        map<char,int>mp;
        for(int i=0;i<s.length();i++)
        {
            mp[s[i]]++;
        }
        int count=0;
        for(auto i:mp)
        {
            if(i.second&1)
            {
                count++;
            }
        }
        if(count<=k)return true;
        return false;
    }
};


# JAVA

import java.util.HashMap;

class Solution {
    public boolean canConstruct(String s, int k) {
        if (s.length() < k) {
            return false;
        }

        HashMap<Character, Integer> charCountMap = new HashMap<>();
        for (int i = 0; i < s.length(); i++) {
            charCountMap.put(s.charAt(i), charCountMap.getOrDefault(s.charAt(i), 0) + 1);
        }

        int oddCount = 0;
        for (int count : charCountMap.values()) {
            if (count % 2 != 0) {
                oddCount++;
            }
        }

        return oddCount <= k;
    }
}



#Python



class Solution:
    def canConstruct(self, s: str, k: int) -> bool:
        if len(s) < k:
            return False

        # Count the frequency of each character
        char_count = {}
        for char in s:
            char_count[char] = char_count.get(char, 0) + 1

        # Count the number of characters with odd frequencies
        odd_count = sum(1 for count in char_count.values() if count % 2 != 0)

        return odd_count <= k
