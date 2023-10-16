# Rubyのドリルを解いていく
### 課題
前回のドリルで作成したアプリケーションにデータ登録、呼び出し機能を追加する。

#### 前回までのコード
```
def register_data
  puts '名前を入力してください'
  puts 'パンチ力を入力してください(0 ~ 100)'
  puts 'キック力を入力してください(0 ~ 100)'
  puts 'ジャンプ力を入力してください(0 ~ 100)'

end

def show_data_list
  puts '見たい人の番号を選択してください'
end

while true
  puts '選択してください'
  puts '[0]登録する'
  puts '[1]データを確認する'
  puts '[2]終了する'
  input = gets.to_i

  if input == 0
    register_data
  elsif input == 1
    show_data_list
  elsif input == 2
    exit
  else
    puts '無効な値です'
  end
end
```

### 仕様
- def register_dataメソッドで情報を入力させ、ハッシュに格納したあと、配列に格納するコードを書きましょう。
　登録する情報は、名前,パンチ力,キック力,ジャンプ力です。
　力は1~100までの数値で入力させます。
　1~100以外の値が入力された場合は”100以下の数字を入力してください”と表示し、入力フェーズに戻るようにします。
- show_data_listメソッドで、登録した情報から名前だけを取り出して一覧表示させましょう。

### 回答
```
def register_data
  puts '名前を入力してください'
  name = gets.chomp
  puts 'パンチ力を入力してください(0 ~ 100)'
  punch = power(gets.to_i)
  puts 'キック力を入力してください(0 ~ 100)'
  kick = power(gets.to_i)
  puts 'ジャンプ力を入力してください(0 ~ 100)'
  jump = power(gets.to_i)

  person = {name: name, punch: punch, kick: kick, jump: jump}
  data << person

end

def power(power)
  while power > 100
    puts '100以下の数字を入力してください'
      power = gets.to_i
  end
  return power
end

def show_data_list(data)
  puts '見たい人の番号を選択してください'
  data.each_with_index do |person, index|
    puts "#{index + 1}: #{person[:name]}"
  end
  input = gets.to_i - 1
  person = data[input]
  puts "名前: #{person[:name]}"
  puts "パンチ力: #{person[:punch]}"
  puts "キック力: #{person[:kick]}"
  puts "ジャンプ力: #{person[:jump]}"
  
end



while true
  puts '選択してください'
  puts '[0]登録する'
  puts '[1]データを確認する'
  puts '[2]終了する'
  input = gets.to_i

  if input == 0
    register_data
  elsif input == 1
    show_data_list
  elsif input == 2
    exit
  else
    puts '無効な値です'
  end
end
```

### 模範解答
```
def register_data(data)
  puts '名前を入力してください'
  name = gets.chomp
  puts 'パンチ力を入力してください(0 ~ 100)'
  punch = power(gets.to_i)
  puts 'キック力を入力してください(0 ~ 100)'
  kick = power(gets.to_i)
  puts 'ジャンプ力を入力してください(0 ~ 100)'
  jump = power(gets.to_i)

  person = {name: name, punch: punch, kick: kick, jump: jump}
  data << person

end

def power(power)
  while power > 100
    puts '100以下の数字を入力してください'
      power = gets.to_i
  end
  return power
end

def show_data_list(data)
  puts '見たい人の番号を選択してください'
  data.each_with_index do |person, index|
    puts "#{index + 1}: #{person[:name]}"
  end
  input = gets.to_i - 1
  person = data[input]
  puts "名前: #{person[:name]}"
  puts "パンチ力: #{person[:punch]}"
  puts "キック力: #{person[:kick]}"
  puts "ジャンプ力: #{person[:jump]}"
  
end

data = []

while true
  puts '選択してください'
  puts '[0]登録する'
  puts '[1]データを確認する'
  puts '[2]終了する'
  input = gets.to_i

  if input == 0
    register_data(data)
  elsif input == 1
    show_data_list(data)
  elsif input == 2
    exit
  else
    puts '無効な値です'
  end
end
```

### レビュー
1. data = [] を記述し忘れており、配列を入れる場所がなかった。
2. 各メソッドに引数を渡すための(data)の記述を忘れているため、エラーが発生していた。

