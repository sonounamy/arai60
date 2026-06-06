# arai60

[LeetCode](https://leetcode.com) の問題集 [Arai60](https://1kohei1.com/leetcode/) を使ったコーディング練習のリポジトリ。

言語: Python

---

## 環境セットアップ

```bash
pip install pytest
```

VS Code 拡張:
- [LeetCode](https://marketplace.visualstudio.com/items?itemName=LeetCode.vscode-leetcode) — 問題の閲覧・提出をVS Code内で完結できる

---

## 進め方

### ブランチ運用

問題ごとにブランチを切って作業し、`main` へ PR を出す。

```
{問題番号}/{問題名}
```

例：`387/First-Unique-Character-in-a-String`

### ファイル構成

```
problems/
└── 387/
    ├── solution.py   # gitignore済み・作業用（コミットしない）
    ├── test.py       # テストコード（コミットする）
    └── memo.md       # 解説・気づき
```

### 各問題の取り組み方

**step 1**
- 自力で `solution.py` を書く（目安30分）
- `pytest problems/387/test.py` でテストを通す
- 通ったら `test.py` と `memo.md` をコミット

**step 2**
- 他の人の解答や解説を読む
- 別解・気づきを `memo.md` に追記してコミット

**step 3**
- 何も見ずにもう一度 `solution.py` を書く
- スムーズに書けたら完了・PR を出す

### テストの書き方

```python
# test.py
from solution import Solution

def test_example():
    sol = Solution()
    assert sol.firstUniqChar("leetcode") == 0
    assert sol.firstUniqChar("aabb") == -1
```

```bash
pytest problems/387/test.py
```

### PR の出し方

- タイトル：`387 First Unique Character in a String`

---

## diary

`diary/` フォルダに学習記録や気づきをまとめる。  
ファイル名は `YYYY-MM-DD.md` 形式。

---

## リンク

- [Arai60 問題リスト](https://1kohei1.com/leetcode/)
- [LeetCode](https://leetcode.com)
