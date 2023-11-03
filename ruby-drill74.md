# Rubyのドリルを解いていく
### 課題
問題 74 バブルソート問題2<br>
本ドリルでは、配列の要素である数値を、大きい順に並べ替えて出力するプログラムを実装します。

### 問題
以下の要件を満たすbubble_sortメソッドを実装しましょう。

- 要素が数値である配列を受け取り、数値の大きい順に並べ替えること
- 大きい順に並べ替えた結果を出力すること
- 
#### ひながた
```ruby
def bubble_sort(data)
  # 配列の数を数える処理を記述
  length = 

  # for文を2つ使用する
  # 先頭から隣の数同士の大きさを比べる
  # 先頭側の要素の方が小さい場合は、配列の位置を隣同士で交換する
end

# 呼び出し例
number = [1,23,4,6,12,45,79]
bubble_sort(number)
puts number
```

### 回答
```ruby
def bubble_sort(data)
 
  length = data.length

  for i in 0..(length-1)
    for j in 1..(length-i-1)
      if data[j-1] < data[j]
        data[j-1] , data[j] = data[j] , data[j-1]
      end
    end
  end
end

number = [1,23,4,6,12,45,79]
bubble_sort(number)
puts number
```

### 模範解答
```ruby
def bubble_sort(data)
  length = data.length 
  for i in 0..(length-1) 
    for j in 1.. (length-i-1) 
      if data[j-1] < data[j] 
        data[j-1],data[j] = data[j],data[j-1] 
      end
    end
  end
end

number = [1,23,4,6,12,45,79]

bubble_sort(number)

puts number
```
### レビュー
- 今回はひな型のヒントが少なかったが、模範解答と同じようにコードを書くことができた。
- 配列の要素は先頭を0番目とカウントするので「length(配列の要素の数)-1」となっていることに注意できている。
