# 142. Linked List Cycle II

https://leetcode.com/problems/linked-list-cycle-ii/

## 取り組み方

- step1: 5分考えて分からなかったら答えを見る。答えを理解したら、答えを隠して書く。筆が進まず5分立ったら答えを見る。答えを送信して正解するまで。
- step2: コードを読みやすく整える。動くコードになったら終了。
- step3: 時間を計りながら書く。10分以内に3回連続でアクセプトされるまで。

# step1

## 方針を考える

- visitedをsetで保存していって、最初に被ったものを出力、なければNone

## 実装

```python
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        visited = set()
        while head is not None:
            if head in visited:
                return head
            visited.add(head)
            head = head.next
        return None
```

## バグ

- `visited.add(head)` を書き忘れて無限ループした

## 気づき・疑問

- `2, 2, 2, 2` のようにvalが全部同じノードでも正しく動くか？
  - Pythonでは `__eq__` / `__hash__` を定義していない場合、デフォルトでオブジェクトのID（メモリアドレス）で比較・ハッシュされる
  - 同じvalでも `ListNode(2)` を別々に作れば別オブジェクト（別アドレス）なので、setで正しく区別できる
  - `id(a)` で確認できる

# step2

```python
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        visited = set()
        while head is not None:
            if head in visited:
                return head
            visited.add(head)
            head = head.next
        return None
```

特に改善が思いつかず、変化なし。

# step3

```python
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        visited = set()
        current = head
        while current is not None:
            if current in visited:
                return current
            visited.add(current)
            current = current.next
        return None
```

- 先頭nodeでないものが変数headに次々と代入されていくのは不自然と感じたので、現在見ているnode: currentに変数名を変更
上記コードを何も見ずスムーズに繰り返し書ける状態に

## 気づき（他の人のPRより）

- 参考: https://github.com/shintaro1993/arai60/pull/5/changes

- set の `x in set` の計算量
  - hash値から一候補を計算して確認するため、基本的にはO(1)。ただしhash値が必ず同じになるinstanceだけでsetの要素が構成されるという例外的な状況下では最悪O(n)
  - 参考: [Time Complexity](https://wiki.python.org/moin/TimeComplexity)
