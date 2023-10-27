# Rubyのドリルを解いていく
### 課題
カロリー計算のプログラムをつくりましょう。以下のような仕様です。

- メニュー画面ではカロリーを入力か、カロリーの合計を見るか選べます
- カロリーを入力の場合、料理名とカロリーを入力します
- 入力後はメニューに戻り、続けてカロリーを入力か、カロリーの合計を見るかを選べます
- カロリーの合計を見るを選んだら全ての料理名とカロリーを表示して、最後にカロリーの合計を表示します
- カロリーの合計を見たらプログラムを終了します
#### メニュー画面（ターミナル）
```
[0]:カロリーを入力する
[1]:カロリーの合計を見る
```
#### カロリー入力画面（ターミナル）
```
料理名を入力してください:
スパゲティ
カロリーを入力してください:
720
```
#### カロリー合計表示画面（ターミナル）
```
-----------------------------
メロンパン  :430kcal
スパゲティ  :720kcal
バナナ  :80kcal
-----------------------------
カロリー合計  :1230kcal
```

#### ひな型
```ruby
class Food
    # ここにクラスの定義を書き加えてください
  end

  while true do
    puts "[0]:カロリーを入力する"
    puts "[1]:カロリーの合計を見る"
    input = gets.to_i

    if input == 0
      Food.input           # カロリーの入力
    elsif input == 1
      Food.show_all_calory # カロリーの合計を表示
      exit
    end
  end
```

### 回答
```ruby
class Food
  @@foods = []

  def self.input
    puts "料理名を入力してください："
    name = gets.chomp
    puts "カロリーを入力してください："
    calory = gets.to_i
    
    food = Food.new(name, calory)

    @@foods << food
  end

  def self.show_all_calory
    all_calory = 0
    line = "-----------------------------"
    puts line
    @@foods.each do |food|
      puts "#{food.name} :#{food.calory}"
      all_calory += food.calory
    end
    puts line
      puts "カロリー合計： #{all_calory}"
  end

  def initialize(name, calory)
    @name= name
    @calory = calory
  end

end

while true do
  puts "[0]:カロリーを入力する"
  puts "[1]:カロリーの合計を見る"
  input = gets.to_i

  if input == 0
    Food.input           # カロリーの入力
  elsif input == 1
    Food.show_all_calory # カロリーの合計を表示
    exit
  end
end
```

### 模範解答
```ruby
class Food
  @@foods = []

  def self.input
    puts "料理名を入力してください："
    name = gets.chomp
    puts "カロリーを入力してください："
    calory = gets.to_i
    
    food = Food.new(name, calory)

    @@foods << food
  end

  def self.show_all_calory
    all_calory = 0
    line = "-----------------------------"
    puts line
    @@foods.each do |food|
      puts "#{food.name} :#{food.calory}"
      all_calory += food.calory
    end
    puts line
      puts "カロリー合計： #{all_calory}"
  end

  def initialize(name, calory)
    @name= name
    @calory = calory
  end

  def name
    return @name
  end

  def calory
    return @calory
  end
  

end

while true do
  puts "[0]:カロリーを入力する"
  puts "[1]:カロリーの合計を見る"
  input = gets.to_i

  if input == 0
    Food.input           # カロリーの入力
  elsif input == 1
    Food.show_all_calory # カロリーの合計を表示
    exit
  end
end
```

### レビュー
[1]カロリーの合計を見るでエラーが出てしまったが、解決方法がわからなかったので、模範解答をカンニングするまでを自力で行った部分を回答に記載。<br>
クラスメソッド：input、show_all_caloryの定義はよくできた。<br>
料理名とカロリー情報をインスタンスで持つために、Foodクラスでインスタンス@nameと@caloryを定義する必要があった。<br>
そのため、initializeメソッドで
```
@name = name
@calory = calory
```
と定義する。<br>
インスタンスを生成 Food.new(name, calory) し
一覧で表示するために、このインスタンスを```@@foods```で定義したクラス変数で保存する。
```
@@foods << food
```
##### 次からわからなかった部分
foodインスタンスの料理名はインスタンス変数```@name```、カロリーはインスタンス変数```@calory```。<br>
これらを取得するためのインスタンスメソッドnameとcaloryを実装する。<br>
↑この部分インスタンスメソッドを定義しないと、<br>
```
undefined method `name' for #<Food:0x000055f36f554bb0 @name="2222", @calory=2222> (NoMethodError)
```
となる。
インスタンス変数になっているのでnameとしても値を返すことができないので@name=nameでnameがインスタンス変数である@nameだということを定義しておかないといけない？
もうすこしクラスとインスタンスについて復習する必要があると感じた。



