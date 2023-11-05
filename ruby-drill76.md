# Rubyのドリルを解いていく
### 課題
以下の要件を満たすtext_transformメソッドを実装しましょう。

- 対象となる文字列から空白を削除すること
- 対象となる文字列が小文字だった場合、大文字に置換すること
- 空白が含まれない大文字の文字列を出力すること

### ひな型
```ruby
def text_transform(text)
  # 処理を記述
end

# 呼び出し例
text_transform("hello world")
```

### 回答
```ruby
def text_transform(text)
  text = text.gsub(/[\s　]/,"")
  text = text.upcase
  puts text
end

text_transform("hello world")
```

### 模範解答
```ruby
def text_transform(text)
  puts text.gsub(/[\s　]/, "").upcase
end

text_transform("hello world")
```

### レビュー
upcaseまで続けて処理をひとまとめにした方が、すっきりする。
