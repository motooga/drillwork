# Rubyのドリルを解いていく
### 課題
前回のドリルで作成したアプリケーションにデータ登録、呼び出し機能を追加する。
以下の仕様を満たすアプリケーションを作成してください。また、必ず注意書きを読んでから作成に取り掛かってください。

 ### 仕様
- プログラムを実行すると、以下の3つの選択肢が表示され、直後にユーザーに対して値の入力を求めること。
[1] : 商品を登録する
[2] : 商品の利益一覧を確認する
[3] : アプリを終了する
[1]を選択した場合は、商品名、販売価格、仕入れ値を入力させ、保存する。
[2]を選択した場合は、保存された全ての商品情報（商品名・販売価格・仕入れ値）と、それぞれの利益・利益率を計算し、商品ごとに一覧表示する。直後に、全ての商品の合計（総売上・総利益・平均利益率）を表示する。ただし、利益率は四捨五入して、小数点2桁まで表示する。
[3]を選択した場合は、アプリケーションを終了する。
アプリケーションを終了するまで、処理を繰り返すこと。
- 前回からの変更点
今回新たに追加実装してもらう機能は主に以下の2点です。

- 商品ごとの利益・利益率を表示させる
- 商品の合計（総売上・総利益・平均利益率）を表示させる

注意
- 雛形を使用すること
- 引数は雛形で考慮していないため、必要に応じて引数を設定すること
- 正しく動作している箇所までが採点対象となるため、必ず動作確認しながら進めること
- エラーはインターネットで調べるなどして解決すること
- エラーが出たままその先の実装をしないこと

### ひながた

```ruby
def register_item(registered_item)
  item = {}
  puts "商品名を入力してください："
  item[:name] = gets.chomp
  puts "販売価格を入力してください："
  item[:selling_price] = gets.to_i
  puts "仕入れ値を入力してください："
  item[:cost_price] = gets.to_i
  line = "---------------------------"

  puts "商品名 : #{item[:name]}\n#{line}"
  puts "販売価格 : #{item[:selling_price]}円\n#{line}"
  puts "仕入れ値 : #{item[:cost_price]}円\n#{line}"

  registered_item << item

  return registered_item
end

def calculate_profit(item)
  # 保存された商品の情報を元に、利益と利益率を計算する

end

def check_items(registered_item)
  # 保存された全ての商品情報（商品名・販売価格・仕入れ値）と、それぞれの利益・利益率を計算し、商品ごとに表示する
  line = "---------------------------"
  puts "【商品一覧】\n#{line}"

  registered_item.each do |item|
    puts "商品名：#{item[:name]}"
    puts "販売価格：#{item[:selling_price]}円"
    puts "仕入れ値：#{item[:cost_price]}円"
    puts "利益：円"
    puts "利益率：%\n#{line}"
  end

  # 全ての商品の合計（総売上・総利益・平均利益率）を表示する
  puts "【合計】\n#{line}"
  puts "総売上 : 円"
  puts "総利益 : 円"
  puts "平均利益率 : %\n#{line}"

end

def end_program
  exit
end

def exception
  puts "入力された値は無効な値です"
end

item_list = []

while true do
  puts "商品数: #{item_list.length}"
  puts "[1]商品を登録する"
  unless item_list.empty?
    puts "[2]商品の利益一覧を確認する"
  end
  puts "[3]アプリを終了する"

  input = gets.to_i

  if input == 1 then
    item_list = register_item(item_list)
  elsif input == 2 then
    check_items(item_list)
  elsif input == 3 then
    end_program
  else
    exception
  end
end
```

### 回答
```ruby
def register_item(registered_item)
  item = {}
  puts "商品名を入力してください："
  item[:name] = gets.chomp
  puts "販売価格を入力してください："
  item[:selling_price] = gets.to_i
  puts "仕入れ値を入力してください："
  item[:cost_price] = gets.to_i
  line = "---------------------------"

  puts "商品名 : #{item[:name]}\n#{line}"
  puts "販売価格 : #{item[:selling_price]}円\n#{line}"
  puts "仕入れ値 : #{item[:cost_price]}円\n#{line}"

  registered_item << item

  return registered_item
end

def calculate_profit(item)
  item[:profit] = item[:selling_price] - item[:cost_price]
  item[:profit_rate] = ((item[:profit] / item[:selling_price]).to_f *100).round(2)
  return item
end

def check_items(registered_item)
  # 保存された全ての商品情報（商品名・販売価格・仕入れ値）と、それぞれの利益・利益率を計算し、商品ごとに表示する
  line = "---------------------------"
  puts "【商品一覧】\n#{line}"
  sum_profit = 0
  sum_selling_price = 0
  sum_profit_rate = 0

  registered_item.each do |item|
    puts "商品名：#{item[:name]}"
    puts "販売価格：#{item[:selling_price]}円"
    puts "仕入れ値：#{item[:cost_price]}円"
    calculate_profit(item)
    puts "利益：#{item[:profit] }円"
    puts "利益率：#{item[:profit_rate] }%\n#{line}"
    sum_selling_price += item[:selling_price]
    sum_profit += item[:profit]
    sum_profit_rate += item[:profit_rate]
  end
  average_profit_rate =  sum_profit_rate / register_item.length
  puts "【合計】\n#{line}"
  puts "総売上 : #{sum_selling_price}円"
  puts "総利益 : #{sum_selling_price}円"
  puts "平均利益率 : #{average_profit_rate}%\n#{line}"

end

def end_program
  exit
end

def exception
  puts "入力された値は無効な値です"
end

item_list = []

while true do
  puts "商品数: #{item_list.length}"
  puts "[1]商品を登録する"
  unless item_list.empty?
    puts "[2]商品の利益一覧を確認する"
  end
  puts "[3]アプリを終了する"

  input = gets.to_i

  if input == 1 then
    item_list = register_item(item_list)
  elsif input == 2 then
    check_items(item_list)
  elsif input == 3 then
    end_program
  else
    exception
  end
end
```

### 模範解答

```ruby
def register_item(registered_item)
  item = {}
  puts "商品名を入力してください："
  item[:name] = gets.chomp
  puts "販売価格を入力してください："
  item[:selling_price] = gets.to_i
  puts "仕入れ値を入力してください："
  item[:cost_price] = gets.to_i
  line = "---------------------------"

  puts "商品名 : #{item[:name]}\n#{line}"
  puts "販売価格 : #{item[:selling_price]}円\n#{line}"
  puts "仕入れ値 : #{item[:cost_price]}円\n#{line}"

  registered_item << item

  return registered_item
end

def calculate_profit(item)
  # 保存された商品の情報を元に、利益と利益率を計算する
  profit = item[:selling_price] - item[:cost_price]
  profit_rate = profit.to_f / item[:selling_price].to_f

  item[:profit] = profit
  item[:profit_rate] = profit_rate
  return item
end

def check_items(registered_item)
  # 変数の定義
  total_profit = 0
  total_sales = 0

  # 保存された全ての商品情報（商品名・販売価格・仕入れ値）と、それぞれの利益・利益率を計算し、商品ごとに表示する
  line = "---------------------------"
  puts "【商品一覧】\n#{line}"

  registered_item.each do |item|
    item = calculate_profit(item) # 利益計算のために、calculate_profitメソッドの呼び出し
    puts "商品名：#{item[:name]}"
    puts "販売価格：#{item[:selling_price]}円"
    puts "仕入れ値：#{item[:cost_price]}円"
    puts "利益：#{item[:profit]}円"
    puts "利益率：#{(item[:profit_rate] * 100).round(2)}%\n#{line}"

    total_profit += item[:profit]
    total_sales += item[:selling_price]
  end

  # 全ての商品の合計（総売上・総利益・平均利益率）を表示する
  profit_avarage = total_profit.to_f / total_sales.to_f
  puts "【合計】\n#{line}"
  puts "総売上 : #{total_sales}円"
  puts "総利益 : #{total_profit}円"
  puts "平均利益率 : #{(profit_avarage * 100).round(2)}%\n#{line}"
end

def end_program
  exit
end

def exception
  puts "入力された値は無効な値です"
end

item_list = []

while true do
  puts "商品数: #{item_list.length}"
  puts "[1]商品を登録する"
  unless item_list.empty?
    puts "[2]商品の利益一覧を確認する"
  end
  puts "[3]アプリを終了する"

  input = gets.to_i

  if input == 1 then
    item_list = register_item(item_list)
  elsif input == 2 then
    check_items(item_list)
  elsif input == 3 then
    end_program
  else
    exception
  end
end
```

### レビュー
doril72.rb:22:in `to_f': wrong number of arguments (given 1, expected 0) (ArgumentError)
のエラーを解決できなかった。
```ruby
def calculate_profit(item)
  # 保存された商品の情報を元に、利益と利益率を計算する
  profit = item[:selling_price] - item[:cost_price]
  profit_rate = profit.to_f / item[:selling_price].to_f

  item[:profit] = profit
  item[:profit_rate] = profit_rate
  return item
end
```
計算中は変数として扱い最終的にハッシュに追加する方が式が綺麗になる<br>
平均利益率の計算が間違えていた。
```ruby
profit_avarage = total_profit.to_f / total_sales.to_f
```
