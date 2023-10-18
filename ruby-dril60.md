# Rubyのドリルを解いていく
### 課題
クラスを使用して以下の表示結果を出力するコードを記述しましょう。
#### 仕様
1. クラス変数

| 変数名 | 値 |
| :---: | :---: |
| type | 犬 |
   
2. インスタンス変数
   
 | 変数名 | 値 |
 | :---: | :---: |
 | name | マロン|
 | dog_type | トイプードル　|
 
 
3. クラスメソッド

| メソッド名 | 処理 |
| :---: | :--- 
| say | "ワンワン"とターミナルに出力 |

4. インスタンスメソッド

| メソッド名 | 処理 |
| :---: | :---: |
|say_type|"私は「クラス変数type」です"とターミナルに出力|
|self_introduction|"私の名前は「インスタンス変数name」で種類は「インスタンス変数dog_typeです'とターミナルに出力する|

```ひな型
 class Dog
    # ここにクラスの定義を書き加えてください
  end

  # クラスの外でメソッドを呼び出してください
```

### 回答

```ruby
class Dog
  @@type = "犬"

  def self.say
    puts "ワンワン"
  end

  def say_type
    puts "私は#{@@type}です"
  end

  def self_introduction
    @name = "マロン"
    @dog_type = "トイプードル"
    puts "わたしの名前は#{@name}で種類は#{@dog_type}"

  end
  
end
  Dog.say
  Dog.new.say_type
  Dog.new.self_introduction
  
```

### 模範解答

```ruby
class Dog
    @@type = "犬"

    def initialize
      @name = "マロン"
      @dog_type = "トイプードル"
    end

    def self.say
      puts "ワンワン"
    end

    def say_type
      puts "わたしは#{@@type}です"
    end

    def self_introduction
      puts "わたしの名前は#{@name}で種類は#{@dog_type}です"
    end
  end

 dog = Dog.new
 Dog.say
 dog.say_type
 dog.self_introduction

```
### レビュー
- インスタンス変数を定義するためのinitializeを定義し忘れていた
- 呼び出し方で何度もDog.newを記述している部分で、工夫が足りなかった。
- クラスメソッドを呼び出すときは問題なし
- インスタンスメソッドを呼び出す際はインスタンスを生成してから呼び出す
