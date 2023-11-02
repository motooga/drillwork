# Rubyのドリルを解いていく bubble_sort
### 課題
本ドリルでは、配列の要素である数値を、小さい順に並べ替えて出力するプログラムを実装します。

### 問題
- 以下の要件を満たすbubble_sortメソッドを実装しましょう。

- 要素が数値である配列を受け取り、数値の小さい順に並べ替えること
- 小さい順に並べ替えた結果を出力すること

#### ひな型
```ruby
def bubble_sort(data)
  # 配列の数を数える処理を記述
  length = 

  # for文を2つ使用する
  # 先頭から隣の数同士の大きさを比べる
  # 先頭側の要素の方が大きい場合は、配列の位置を隣同士で交換する
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
      if data[j-1] > data[j]
        data[j-1],data[j]=data[j],data[j-1]
      end
    end
  end
end

# 呼び出し例
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
      if data[j-1] > data[j] 
        data[j-1],data[j] = data[j],data[j-1] 
      end
    end
  end
end

number =  [1,23,4,6,12,45,79]

bubble_sort(number)

puts number
```

### レビュー
パーフェクトクリアでした。
bubble_sortという基本的なアルゴリズムの考え方。
他にもソートアルゴリズムはいくつか存在するので覚えておくとデータを扱う実装時に役立つ。
[参考記事](https://zenn.dev/brainyblog/articles/sort-algorithms-explained)



