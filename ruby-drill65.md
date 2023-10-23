# Rubyのドリルを解いていく
### 課題
プログラムとじゃんけんをするプログラムを作ってください。
- 勝った場合 "あなたの勝ちです"と表示させる
- 負けた場合 "あなたの負けです"と表示させる
- あいこの場合 "あいこで"と表示させたあともう一度じゃんけんをさせる

#### ひな型

```ruby
def janken
  puts "[0]:グー\n[1]:チョキ\n[2]:パー"

  # ターミナルからじゃんけんの手を入力
  player_hand = 

  # 乱数でプログラム側の手を決定
  program_hand = 

  jankens = ["グー", "チョキ", "パー"]

  puts "あなたの手:#{jankens[player_hand]}, わたしの手:#{jankens[program_hand]}"

  # あいこの判定はplayer_handとprogram_handの値が等しいとき
  if 
    puts "あいこで"
    # 返り値を返す

 # じゃんけんに勝つパターンを全て並べる
  elsif
    puts "あなたの勝ちです"
   # 返り値を返す

  else
    puts "あなたの負けです"
    # 返り値を返す

  end
end

next_game = true

puts "最初はグー、じゃんけん..."

while next_game do
# jankenメソッドの返り値をnext_gameに代入
end
```

### 回答

```ruby
def janken
  puts "[0]:グー\n[1]:チョキ\n[2]:パー"
  player_hand = gets.to_i

  program_hand = rand(3)

  jankens = ["グー", "チョキ", "パー"]

  puts "あなたの手:#{jankens[player_hand]}, わたしの手:#{jankens[program_hand]}"


  if player_hand == program_hand
    puts "あいこで"
    return true

  elsif (player_hand == 0 && program_hand == 1) || (player_hand == 1 && program_hand == 2) || (player_hand == 2 && program_hand == 0) 
    puts "あなたの勝ちです"
    return false

  else
    puts "あなたの負けです"
    return false

  end
end

next_game = true

puts "最初はグー、じゃんけん..."

while next_game do
 next_game = janken
end
```

### 模範解答

```ruby
def janken
  puts "[0]:グー\n[1]:チョキ\n[2]:パー"
  player_hand = gets.to_i

  program_hand = rand(3)

  jankens = ["グー", "チョキ", "パー"]

  puts "あなたの手:#{jankens[player_hand]}, わたしの手:#{jankens[program_hand]}"

  if player_hand == program_hand
    puts "あいこで"
    return true
  elsif (player_hand == 0 && program_hand == 1) || (player_hand == 1 && program_hand == 2) || (player_hand == 2 && program_hand == 0)
    puts "あなたの勝ちです"
    return false
  else
    puts "あなたの負けです"
    return false
  end
end

next_game = true

puts "最初はグー、じゃんけん..."

while next_game do
  next_game = janken
end
```

### レビュー
- 条件式&&をいつも&としてして間違えてしまうが、今回は&&にすることができた。
- while next_game doの使い方が分からず、ググってしまったので復習
  文法:
  ```ruby
  while 式　[do]
  ・・・
  end
  ```
  式を評価した値が真の間本体を繰り返し実行
  今回の場合jankenメソッド内のif文で返り値が決定しているnext_gameがtrueの場合はnext_game にjankenメソッドが代入されるので、
  trueの間はjankenメソッドが繰り返される。


