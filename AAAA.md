# 第一次社課 重溫Python

看到這個標題時，可能一堆人都已經會Python了。接下來將快速讓大家複習一下Python語法。

## 輸入

Python 所定義的輸入函式如下：

```python=
input([prompt])
```

實際例子：

```python= 
score = input( "請輸入你的成績" )
```

試試看多增加幾個成績然後求總成績吧。

```python=
math = int(input( "請輸入數學成績：" ))
english = int(input( "請輸入英文成績：" ))
sum =  math + english 
print( sum )

```

## 函式

函式就是一臺沒有感情的機器，放入原料（輸入），它就會給予對應的產出（輸出）
舉以下兩個圖片為例：
![](https://i.imgur.com/1wXL4yD.png)

![](https://i.imgur.com/VfoIyFz.png)
圖片來源：https://www.zetria.org/view.php?subj=programming&chap=biououdovn


不對阿，這樣為何不直接複製貼上一段程式碼就好了？ 當然也可以，但是就會像前面迴圈提到的例子一樣，如果真的這麼做了，整個程式碼就會變得又臭又長，既然能簡潔，則何樂而不為？

在查資料時，看到有人整理出函式的優點，而我覺得整理的很有道理，所以跟大家分享：

1. 程式的重複利用性：如果我們想要重複地做一件事，將這個功能寫成函式，不必擔心會不會在複製貼上時出了什麼差錯導致程式碼變成一團混亂。
2. 程式的易讀性：將功能包裝成一個名稱明確的函式，能夠使其他人在閱讀你的程式碼時，更能理解這一個區段所要進行的操作是什麼，增加易讀性。
3. 程式的易除錯性：寫成函式的好處還有較容易 debug 找出其中的錯誤，當發現程式所跑出的結果不如預期時，只需要檢查定義函式時有無差錯即可
4. 程式的一致性：程式學到後面，與其他人一同撰寫一個大型專案是很常遇到的事情，此時如果你將你所寫的這一個功能包裝成一個 function 再傳給別人繼續作業時，就比較不會更動到這個函式當中的內容，後續進行維護也較為容易。
5. 程式的模組化：模組化是一個在撰寫程式時的概念，如果將寫一個完整的程式視為蓋一棟房子，那麼函式就像是房子的鋼筋、水泥、磚塊這樣的東西。程式是由許多個函式以及其他東西所建構出來的，而且函式與函式之間的分工十分明確，每一個函式有它自己所負責的東西。

而以上種種就造就出函式的優點

說了那麼多，準備進入我們的實戰環節，函式的基本架構如下：
```python=
    def 函式名稱(參數):
        程式碼
```

繼續沿用前面的例子：
我今天想要做個輸入成績就能判斷是否及格的程式，同時也將輸入的成績總和並看總平均是否及格：
```python=
def main():
    math = int(input( "請輸入您的數學成績： " ))
    isPass(math)
    english = int(input( "請輸入您的英文成績： " ))
    isPass(english)
    chinese = int(input( "請輸入您的國文成績： " ))
    isPass(chinese)

    sum = math + english + chinese 
    average = sum / 3 
    print( "總平均：", average )
    isPass( average )


def isPass( score ):
    if score >= 60 :
        print( "恭喜你及格了" )
        return True
    elif score < 60 :
        print( "好的課值得一修再修" )
        return False 
    
main()
```


## import 
import 就像玩遊戲的插件，你可以增加額外的功能進去，
最基礎的用法就是：
```python=
import 模組名稱
import 模組名稱 as 縮寫 # 這樣就可以減少打字的數量
# 像是PyTorch 可以縮寫成 pt
# TensorFlow可以縮寫成tf
# Numpy可以縮寫成np
# 但必須注意的是 縮寫必須讓別人看的懂
```

再稍微進階，如果該模組你只想要用其中一種功能的話：
```python=
from 模組名稱 import 方法 
```

:::danger
請注意 : 若是使用 from 模組名稱 import 方法 會將該模組名稱的方法直接導入全域命名空間中，可以不需要用`模組名稱.方法`的方式來呼叫，但可能會導致命名衝突，並讓程式碼難以理解。
因此，一般建議使用 import 模組名稱
:::

來試試看實際的例子吧：
``` =python
from random import randint
# 從 random 模組中，引入 randint 函數
```
從字面上猜測，他應該可以產生出隨機的數而官方文件中提示的用法如下：
```=python 
random(開始值, 停止值)
```

有了這些資訊，我們來使用看看吧！

實際例子：
```=python
import random
test = random.randint( 1, 9 )
print(test)
```
```=python
from random import randint 
test = randint( 1, 9 )
print(test)
```

透過額外的模組，可以讓 Python 變得更強大與方便

## OOP in Python

:::info
相信大家都已經對Python基礎語法再熟悉不過了，但是對於非資工/資管相關的人來說，OOP可說是非常陌生。但既然Python是物件導向的語言，怎麼可能跳過OOP呢?
之後的課程，會大量的使用自己寫的，或者是別人寫的物件，因此必須要熟悉。
:::

![](https://img-9gag-fun.9cache.com/photo/a3wYoXm_460s.jpg)
### 淺談物件

物件導向是利用軟體模擬現實生活中的實體，程式內稱為「物件」，每個物件可以有自己的"屬性"以及"方法"。
四大觀念 : class(類別)、object(物件)、method(方法)、property(屬性)
三大特性 : Encapsulation(封裝)、Inheritance(繼承)、Polymorphism(多型)

接下來給一份範例code
```python=
class Dog:
    
    def __init__(self,name,gender,weight,height,color):
        self.name = name
        self.gender = gender
        self.weight = weight
        self.height = height
        self.__color = color
    
    def getColor(self):
        return self.__color
        
dog = Dog("Lucky","male",600,10000,"blue")

print(dog.weight) # 取 public member 可以正常取
# print(dog.__color) # 無法直接取得Private member
print(dog.getColor()) # 可以透過getter method取得private member
print(dog._Dog__color) # 魔術
```

現在來一一介紹上面的程式在幹嘛

#### 建構子

建構子語法如下：
`def __init__(self, 其他參數):`
就算是在建構子裡面`self`也是必須傳入的參數喔！

值得一提的是Python**不支援多建構子(multi constructor)**，但是可以透過預設值的方式來達成！
`def __init__(self, para1=”para1預設值”, para2=”para2預設值2″):`
如此一來，就可以有3種宣告方式！

使用類別**自己的變數、函數都須要加上『 self.變數名稱 』才能使用！**

#### class method

顧名思義，就是在class內寫的function。**請記得要在最前面的地方加入「self」，否則無法透過.來呼叫**
```python=
class Dog:
    
    def __init__(self,name,gender,weight,height,color):
        self.name = name
        self.gender = gender
        self.weight = weight
        self.height = height
        self.__color = color
    
    def getColor(self):
        return self.__color
        
    def printAaa():
        print("Hello")
dog = Dog("Lucky","male",600,10000,"blue")
Dog.printAaa() # 印出Hello

```

#### 封裝
Python只有public跟private
在Python裡面 若要宣告為private 加上雙底線就可以了 像是 `__color`，但private member可以透過一些旁門左道存取，並不像C++跟Java是真的只能透過class內的method存取。就像本單元最上面的程式碼一樣 透過 dog._Dog__color 取得原本該是private的color

:::success
是否需要封裝，還是要依照需求來做決定
:::

#### 繼承

繼承 (Inheritance) 在物件導向中，算是不可或缺的特性。繼承可以使程式碼更加模組化、並且增加可維護和可擴展性。

```python=
class Animal:
    def __init__(self, name):
        self.name = name
        
    def make_sound(self):
        pass
    
class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)
        self.breed = breed
        
    def make_sound(self):
        return "Woof!"

class Cat(Animal):
    def __init__(self, name, color):
        super().__init__(name)
        self.color = color
        
    def make_sound(self):
        return "Meow!"

my_dog = Dog("Fido", "Labrador")
print(my_dog.name)
print(my_dog.breed)
print(my_dog.make_sound())

my_cat = Cat("Whiskers", "Gray")
print(my_cat.name)
print(my_cat.color)
print(my_cat.make_sound())
```

上述例子中，Animal是父類別，而Dog跟Cat式子類別。他們都共同有name這個變數，但只有Dog跟Cat擁有color，意即**父類別有的東西子類別一定有，子類別有的東西父類別不一定有。**(有點像你爸爸的錢你可以亂花，你的錢你爸爸不能亂拿)

`super()`是可以去存取和呼叫父類別的屬性和方法，而不需要知道父類別的名稱。這樣可以減少程式碼的使用。

:::info
因為社課時間有限，並不會介紹多型 (Polymorphism) 和帶領大家使用多型。若對於多型有興趣的人可以去網路上找教材或者利用課餘時間跟我討論。
:::

#### 練習
現在請寫出一個學生類別，裡面有名字、學號、系級、性別、總平均成績，並且寫出 Getter & Setter method，來去存取上述的member。
並且在main當中設計能存放Student類別的list，並且逐行印出學生的資訊。



