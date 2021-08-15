## 简单

### HashMap小结

本质是Entry数组，Entry包含key和value，key获取hash值，会落在hash%entry.length位置上。
hash冲突时，使用拉链法，1.8后当冲突时的元素超过8个，会变成红黑树。


### 有效的字母异位词

主要考察对map的使用
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length()!=t.length()) return false;
        
        int[] map = new int[26];

        for(int i=0; i<s.length();i++){
           
            map[s.charAt(i)-'a']++;
            map[t.charAt(i)-'a']--;
        }

        for(int i=0;i<26;i++){
            if(map[i]!=0) return false;
        }

        return true;
    }
}
```
### n叉树的前序遍历

使用栈的方式
```java
class Solution {
    List<Integer> res = new ArrayList<>();
    public List<Integer> preorder(Node root) {
        if(root==null) return res;

        // 根左右
        Stack<Node> stack = new Stack<>();

        stack.push(root);

        while(!stack.empty()){
            Node node = stack.pop();

            res.add(node.val);

            for(int i=node.children.size()-1;i>=0;i--){
                stack.push(node.children.get(i));
            }

        }

        return res;

    }
}
```

## 中等

### 字母异位词分组

```java
class Solution {

    List<List<String>> res = new ArrayList<>();

    public List<List<String>> groupAnagrams(String[] strs) {
        if(strs==null||strs.length==0) return res;

        Map<String,List<String>> map = new HashMap<>();

        for(int i=0; i<strs.length;i++){
            String str = strs[i];
            char[] s = str.toCharArray();
            Arrays.sort(s);
            String sort = new String(s);
            if(map.containsKey(sort)){
                map.get(sort).add(str);
            }else{
                List<String> list = new ArrayList<>();
                list.add(str);
                map.put(sort, list);
            }
        }

        return new ArrayList(map.values());
    }
}
```
### 丑数
```java
public int nthUglyNumber(int n) {

        long[] res = new long[n];
        res[0] = 1;
        int cur = 0;

        int i2 = 0, i3=0, i5=0;
        for(int i=1; i<n; i++){
            
            long v2 = res[i2] *2;
            long v3 = res[i3] *3;
            long v5 = res[i5] *5;

            long min = Math.min(v2,Math.min(v3,v5));
            res[++cur] = min;
            if(min==v2) i2++;
            if(min==v3) i3++;
            if(min==v5) i5++;

        }

        return (int)res[n-1];
        
    }

```