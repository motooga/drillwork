# Rubyのドリルを解いていく
### 課題
以下の要件を満たすcheck_indexメソッドを実装しましょう。

- 文字列の中に特定の文字が入っている場合は、「特定の文字◯の位置は、◯番目です」と出力すること
- 文字列の中に特定の文字が入っていない場合は、「特定の文字◯はありません」と出力すること
- 文字列の中に特定の文字が複数入っている場合は、特定の文字が最初に出てきた位置を検知すること
- 特定の文字の位置は、1文字目を「0番目」とカウントすること

### ひな型
```ruby
def check_index(text, search_string)
  # 処理を記述
end

# 呼び出し例
check_index("hello","e")
```
出力例
```
check_index("hello","h") → 特定の文字hの位置は、0番目です
check_index("world","e") → 特定の文字eはありません
check_index("apple","p") → 特定の文字pの位置は、1番目です
```
### 回答
```ruby
def check_index(text, search_string)

  index = text.index(search_string)
  if index == nil
    puts "特定の文字#{search_string}はありません"
  else
    puts "特定の文字#{search_string}の位置は、#{index}番目です。"
  end
end

# 呼び出し例
check_index("hello","e")
check_index("hello","h") 
check_index("world","e")
check_index("apple","p") 

```

### 模範解答
```ruby
def check_index(text, search_string)
  index = text.index(search_string)

  if index
    puts "特定の文字#{search_string}の位置は、#{index}番目です"
  else
    puts "特定の文字#{search_string}は、ありません"
  end
end

# 呼び出し例
check_index("hello","e")
```
### レビュー
条件分岐の際にnilの時を記載したが、indexに値があるときの処理を書いた方が良いようです。
その場合、単にif index と記載すれば中身があるときの条件式となる。

