# 141. Linked List Cycle

https://leetcode.com/problems/linked-list-cycle/

# step1(5分)

## 方針を考える

- 連結リストをたどりながら、すでに訪れたノードに再度到達したらcycleあり、とみなす
- 訪れたノードを記録しておいて、重複したら`True`を返す

## 実装

```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        ans = False
        visited = []
        while head is not None:
            if head.val in visited:
                ans = True
                break
            visited.append(head.val)
            head = head.next

        return ans
```

# step2(3~5分)

## 修正方針
- `ans` 変数が不要。True/Falseを直接returnする方がいい
- `list` より `set` が適切
  - 順番という情報を持たない分、それが不要ならより効率的だと思った
  - しかしどのような場合にどれくらい効率良くなり、それがなぜか、などは現時点でよくわかっていない。そもそも、その辺りがネックになるような大規模なケースでは、今良しとしているところに限界が来るものかもしれない

```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        visited = set()
        while head is not None:
            if head.val in visited:
                return True
            visited.add(head.val)
            head = head.next

        return False
```

# step3(3~5分)

## 修正方針
- 値ではなくノード自体を記録すべき。`head.val` だと値が同じ別ノードで誤判定するので`head.val` → `head` に変更
  - `1 -> 1` などでcycleなしなのに`True`を返す
  - これについては、valがnodeを一意に決定するidのようなものだという謎の思い込みがあったため

```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        visited = set()
        while head is not None:
            if head in visited:
                return True
            visited.add(head)
            head = head.next

        return False
```
