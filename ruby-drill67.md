# Rubyのドリルを解いていく
### 課題
以下の機能が満たされた、アプリケーションを作成してください。

#### 仕様
- プログラムの実行を行うと、
[0]商品をカートに入れる
[1]カートを確認する
[2]アプリを終了する
という選択肢を表示し、ユーザーに入力を求め、その入力に従い以下のような処理を行う。

- [2]でアプリケーションを終了するまで、投稿や閲覧が出来るように繰り返す。

- [0]の処理
1. 商品名、値段、個数をユーザーに入力を行って貰う(入力された値の表示まで行う)。
2. 上記の値の保存を行う。

- [1]の処理
1. 保存された全ての商品情報（商品名・値段・個数）を、商品ごとに表示する。また、全ての商品の合計金額を表示する。
2. (買い物を続ける) メニューの表示まで戻る。

- [2]の処理
1. アプリケーションを終了する。

#### ひな型

```ruby

def post_item(a_cart)
# 商品名・値段・個数の入力を促し、入力された値をハッシュオブジェクトで管理する
  puts "商品名を入力してください："
  puts "値段を入力してください："
  puts "個数を入力してください："

  line = "---------------------------"

# 入力された値（ハッシュオブジェクトで管理している値）と合計金額を表示する
  puts "商品名 : "
  puts "値段 : "
  puts "個数 : "
  puts "合計金額 : "

# ハッシュを配列オブジェクトに追加する

# a_cartをメソッドの呼び出し元に返す

end

def check_items(a_cart)
# 保存された全ての商品情報（商品名・値段・個数）を、商品ごとに表示する

# 全ての商品の合計金額を表示する
  puts "合計金額 : "

end

def end_program
  # プログラムを終了させる
end

def exception
  puts "入力された値は無効な値です"
end

cart = []             # 配列オブジェクトcartの生成

while true do
# メニューの表示
  puts "商品数: #{cart.length}"
  puts "[0]商品をカートに入れる"
  unless cart.empty?       #カートに商品がない場合、[1]は選択不可
    puts "[1]カートを確認する"
  end
  puts "[2]アプリを終了する"
  input = gets.to_i

  if input == 0 then
    cart = post_item(cart)  # post_itemメソッドを呼び出す記述
  elsif input == 1 then
    check_items(cart) # check_itemsメソッドを呼び出す記述
  elsif input == 2 then
    end_program     # end_programメソッドを呼び出す記述
  else
    exception           # exceptionメソッドを呼び出す記述
  end
end
```

### 回答

```ruby
def post_item(a_cart)
    puts "商品名を入力してください："
    name = gets.chomp
    puts "値段を入力してください："
    price = gets.to_i
    puts "個数を入力してください："
    number = gets.to_i
    sum_price = price * number

    cart_item = {name: name, price: price, number: number, sum_price: sum_price}

    line = "---------------------------"


    puts "商品名 : #{cart_item[:name]}"
    puts "値段 : #{cart_item[:price]}"
    puts "個数 : #{cart_item[:number]}"
    puts line
    puts "合計金額 : #{cart_item[:sum_price]}"


    a_cart << cart_item

    return a_cart
  end

  def check_items(a_cart)

    sum_price = 0
  a_cart.each_with_index do |cart_item,i|
    puts "#{i} : #{cart_item[:name]}"
    puts "#{cart_item[:price]}"
    puts "#{cart_item[:number]}"
    sum_price = sum_price + cart_item[:sum_price]
  end
  line = "---------------------------"
  puts line

    puts "合計金額 : #{sum_price}"

  end

  def end_program
    exit
  end

  def exception
    puts "入力された値は無効な値です"
  end

  cart = []            

  while true do

    puts "商品数: #{cart.length}"
    puts "[0]商品をカートに入れる"
    unless cart.empty?      
      puts "[1]カートを確認する"
    end
    puts "[2]アプリを終了する"
    input = gets.to_i

    if input == 0 then
      cart = post_item(cart)  
    elsif input == 1 then
      check_items(cart) 
    elsif input == 2 then
      end_program     
    else
      exception           
    end
  end
```

### 模範解答

```ruby
def post_item(a_cart)
  # 変数の定義
  post = {}
  puts "商品名を入力してください："
  post[:name] = gets.chomp
  puts "値段を入力してください："
  post[:price] = gets.to_i
  puts "個数を入力してください："
  post[:count] = gets.to_i
  line = "---------------------------"

  # レビューの描画
  puts "商品名 : #{post[:name]}\n#{line}"
  puts "値段 : #{post[:price]}\n#{line}"
  puts "個数 : #{post[:count]}\n#{line}"
  puts "合計金額 :#{post[:price] * post[:count]}\n#{line}"

  # 配列オブジェクトに追加
  a_cart << post

  # a_cartをメソッドの呼び出し元に返す
  return a_cart
end

def check_items(a_cart)
  # リストの表示
  total_price = 0
  line = "---------------------------"
  a_cart.each do |post|
    puts "#{post[:name]}/#{post[:price]}/#{post[:count]}\n#{line}"
    total_price += post[:price] * post[:count]
  end
  puts "合計金額 : #{total_price}"
end

def end_program
  exit
end

def exception
  puts "入力された値は無効な値です"
end

cart = []         # 配列オブジェクトcartの生成

while true do
  # メニューの表示
  puts "商品数: #{cart.length}"
  puts "[0]商品をカートに入れる"
  unless cart.empty?
    puts "[1]カートを確認する"
  end
  puts "[2]アプリを終了する"

  input = gets.to_i

  if input == 0 then
    cart = post_item(cart)  # post_itemメソッドの呼び出し
  elsif input == 1 then
    check_items(cart) # check_itemsメソッドの呼び出し
  elsif input == 2 then
    end_program    # end_programメソッドの呼び出し
  else
    exception        # exceptionメソッドの呼び出し
  end
end
```

### レビュー
配列に項目を追加する方法がまだ１通りしか浮かばなかったが、最初にハッシュの受け皿を用意して最初からシンボルで入れれば変数を別に用意しなくて良いので効率的な書き方。
```
post={}
post[:name] = gets.chom
post[:price] = gets.to_i
```
個の書き方を忘れないようにしておく
メソッドの引数の部分をもっと復讐する必要がある。時間がないので後日追記
sum_priceとした部分はハッシュに含めないで毎回計算させた方が良い。
