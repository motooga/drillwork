# Rubyのドリルを解いていく
### 課題
前回のドリルで作成したアプリケーションに、戦闘力判定機能を追加しましょう。

### 前回までのコード
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

### 仕様
- パンチ力,キック力,ジャンプ力の３つの力の合計を戦闘力とし、hero_rank メソッドを作成してABCDの４段階にランク分けします。（範囲は任意で構いません）
- ヒーローランクは、一覧表示で名前,パンチ力,キック力,ジャンプ力と一緒に表示されるようにします。

- ### 回答

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

  status = punch + kick + jump
  rank = hero_rank(status)

  person = {name: name, punch: punch, kick: kick, jump: jump, rank: rank}
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
  puts "ヒーローランク: #{person[:rank]}"

end

def hero_rank(status)
  if status >= 0 || status < 100
    rank = "D"
  elsif status >= 20 || status < 200
    rank = "C"
  elsif status >= 40 || status < 300
    rank = "B"
  elsif status =100
    rank = "A"
  end
  puts rank
  return
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
dataにrankが入れられていないので一覧に出したときにヒーローランク：blankとなってしまったが、自力で配列に追加するやり方を思い出せなかった。

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

  person = {name: name, punch: punch, kick: kick, jump: jump,  rank: hero_rank(punch, kick, jump)}
  data << person
ch + kick + jump
  if power == 300
    rank = 'A'
  elsif 100 <= power && power < 300
    rank = 'B'
  elsif 20 <= power && power < 100
    rank = 'C'
  else
    rank = 'D'
  end

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
  puts "ヒーローランク: #{person[:rank]}"

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
end

def power(power)
    while power > 100
      puts '100以下の数字を入力してください'
        power = gets.to_i
    end
    return power
end


def hero_rank(punch, kick, jump)
 power = punch + kick + jump
  if power == 300
    rank = 'A'
  elsif 100 <= power && power < 300
    rank = 'B'
  elsif 20 <= power && power < 100
    rank = 'C'
  else
    rank = 'D'
  end

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
  puts "ヒーローランク: #{person[:rank]}"

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
1. 配列にrankの項目を追加し、その値にherorankのメソッドを入れる
2. hero_rankメソッドの引数としてpunch,kick,jumpの3つの引数を直接渡すためにhero_rank(punch,kick,jump)とする
3. hero_rankメソッド内でpunch,kick,jumpの合計を求めて条件分岐する
4. 条件式の書き方は
   
| 演算子 | 意味 |
| :------: | :----: |
| &&     |aとbがともに真|
| ｜｜ |  AかつB|
| <= | A<=B AがB以下|
| >= | A>=B AがB以上|

演算子忘れてるのでもう一度復習。メソッドの引数の渡し方と配列の入れ方を復習





