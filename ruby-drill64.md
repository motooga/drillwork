# Rubyのドリルを解いていく
### 課題
今日の日付と曜日を出力するコードを作りましょう

**出力例：**
現在は西暦2020年5月27日（今日の日付が入ります）
水曜日です（今日の曜日が入ります）

### 回答

```ruby
now = Time.new
  wday = ["日", "月","火", "水" ,"木","金", "土"]

  puts "現在は、西暦#{now.year}年#{now.month}月#{now.day}日"
  puts "#{wday[now.wday]}曜日です"
```

### 模範解答

```ruby
now = Time.new
puts "現在は西暦#{now.year}年#{now.month}月#{now.day}日"
week = ["日","月","火","水","木","金","土"]
puts week[now.wday] + '曜日です'
```

### レビュー
よくできました！
調べると、よくt = Time.newとしてt.yearとかで出力するのが一般的なよう。
wdayとした部分もweekの方がわかりやすいので慣例的な命名方法を覚えることが課題。
