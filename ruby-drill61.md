# Rubyのドリルを解いていく
### 課題
以下の使用を満たすアプリケーションを作成する。

### 仕様
- プログラムの実装を行うと
[0]データの登録
[1]データの確認
[2]プログラムの終了
という選択肢を表示し、ユーザーに入力を求め、その入力に従い以下のような処理を行う。
- [0]の処理
1. 車種、1Lあたりの走行可能距離(km/l)、乗車人数の入力をユーザーに入力を行って貰う
2. 上記の値の保存を行う
- [1]の処理
1. 保存した情報から番号と名前で一覧を表示し、見たい車種の番号の入力を求める
2. 入力された個別の車種の名前、1Lあたりの走行可能距離(km/l)、乗車人数の表示を行う

 ### 回答
 
```ruby
def new_car(data)
  puts "車種を入力してください"
  type = gets.chomp
  puts "1L当たりの走行距離（km/l)を入力してください"
  consumption = gets.to_i
  puts "乗車人数を入力してください。"
  number = gets.to_i

  car = {type: type, consumption: consumption, number: number}
  data << car
end

def show_data(data)
  puts "見たい車種の番号を入力してください"
  data.each_with_index do |car,index|
    puts "#{index + 1 }: #{car[:type]}"
  end
  input = gets.to_i - 1
  car = data[input]
  puts "車種: #{car[:type]}"
  puts "燃費: #{car[:consumption]}"
  puts "乗車人数: #{car[:number]}"
  
end

data = []

while true
  puts "選択してください。"
  puts "[0]登録する"
  puts "[1]データを確認する"
  puts "[2]終了する"
  input = gets.to_i

  if input == 0
    new_car(data)
  elsif input == 1
    show_data(data)
  elsif input == 2
    exit
  else
    "無効な値です"
  end
end

```



 ### 模範解答
 
 ```ruby
 def register_data(cars)
  puts "車種の入力をして下さい。"
  type = gets.chomp
  puts "1Lあたりの走行可能距離(km/l)を入力して下さい。"
  fuel_economy = gets.to_f
  puts "乗車可能人数を入力して下さい。"
  capacity = gets.to_i
  car = { type: type, fuel_economy: fuel_economy, capacity: capacity }
  cars << car
end

def show_cars(cars)
  cars.each_with_index do |car, index|
    puts "[#{index}]: #{car[:type]}"
  end
  puts "確認したい番号を入力して下さい。"
  input = gets.to_i
  car = cars[input]
  if car
    show_data(car)
  else
    puts "該当する番号はありません。"
  end
end

def show_data(car)
  puts car[:type]
  puts "1Lあたりの走行可能距離:#{car[:fuel_economy]}km/l"
  puts "乗車人数:#{car[:capacity]}人"
end

cars = []

while true do
  puts "番号を入力して下さい"
  puts "[0]:登録をする"
  puts "[1]:データを確認する"
  puts "[2]:終了する"
  input = gets.chomp

  case input
  when "0"
    register_data(cars)
  when "1"
    show_cars(cars)
  when "2"
    exit
  else
    puts "無効な値です"
  end
end
```

### レビュー
- show_dataのとき該当する番号がなかった時のエラー処理を書き忘れている
- 最初の分岐をcaseで書く方法もある。今回はwhileを使用したがいろいろな書き方をできるようにする。
