# Rubyのドリルを解いていく
### 課題
以下の要件を満たすsum_numberメソッドを実装しましょう。

- 第一仮引数をnとし、第二仮引数をmとすること
- nからmまでの数を足し合わせていき、その総和を出力すること（例：n=1,m=5の場合、総和は1+2+3+4+5=11）
#### ひな型
```ruby
def sum_number(n, m)
  # 処理を記述
end

# 呼び出し例
sum_number(1,10)
```

### 回答
```ruby
def sum_number(n, m)
  sum = 0
  (n..m).each do |n|
    sum = sum + n
   end
  puts sum
end

# 呼び出し例
sum_number(1,10)
```

### 模範解答
```ruby
def sum_number(n, m)
  total = 0 # 総和を代入する変数を、初期値0で定義しておく
  while n <= m   # n<=mの条件を満たす間、処理を繰り返す
    total = total + n # 変数totalに変数nを足す
    n = n + 1
  end
  puts total
end

# 呼び出し例
sum_number(5,15)

```

### レビュー
今回自分の回答では、eachメソッドをの範囲指定を行って記述した。<br>
返り値は問題なくかえってきていたので間違いではない。<br>
範囲が決まっている場合はwhileメソッドを使用することもできる。<br>
模範解答の場合<br>
n <= m　の条件が満たされる間は処理を繰り返すことになっている。<br>
繰り返しの処理では、totalという変数にnを足していくようになっている。<br>
また、nに+1してからループすることで次のループでn+1の値を足すことになる。


