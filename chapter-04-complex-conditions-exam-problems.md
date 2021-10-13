# Chapter 4.2. More Complex Conditions – Exam Problems

The previous chapter introduced you to **nested conditions** in **Python**. Via nested conditions, the program logic in a particular application can be represented using **`if` conditional statements** that are nested one into another. We also explained the more complex **`if-elif-else`** conditional statement that allows selecting from a number of options. Now we are going to solve some practical exercises and make sure we have an in-depth understanding of the material, by discussing a set of more complex problems that had been given to students on exams. Before moving to the problems, let's first recall what nested conditions are:

## Nested Conditions

```python
if condition1:
    if condition2:
        # body
    else:
        # body
```

<table><tr><td><img src="/assets/alert-icon.png" style="max-width:50px" /></td>
<td>Remember that it is not a good practice to write <strong>deeply nested conditional statements</strong> (with more than three levels of nesting). Avoid nesting of more than three conditional statements inside one another. This complicates the code and makes its reading and understanding difficult.</td>
</tr></table>

## If-Elif-Else Conditions

When the program operation depends on the value of a variable, we can do consecutive checks with multiple **`if-elif-else`** blocks:

```python
if condition1:
    # body
elif condition2:
    # body
elif condition3:
    # body
else:
    # body
```

The body can consist of any code, as long as it corresponds to the syntactic particularity of the language and is indented one tab inside.


## Exam Problems

Now, after we refreshed our knowledge on how to use and nested conditional statements to implement more complex conditions and program logic, let's solve some exam problems.

## Problem: On Time for the Exam

A student has to attend **an exam at a particular time** (for example at 9:30 am). They arrive in the exam room at a particular **time of arrival** (for example 9:40 am). It is considered that the student has arrived **on time** if they have arrived **at the time when the exam starts or up to half an hour earlier**. If the student has arrived **more than 30 minutes earlier**, the student has come **too early**. If they have arrived **after the time when the exam starts**, they are **late**.

Write a program that inputs the exam starting time and the time of student's arrival, and prints if the student has arrived **on time**, if they have arrived **early** or if they are **late**, as well as **how many hours or minutes** the student is early or late.

### Input Data

You will receive **four integers** (each on a new line):

- The first line contains the **exam starting time (hours)** – an integer from 0 to 23
- The second line contains the **exam starting time (minutes)** – an integer from 0 to 59.
- The third line contains the **hour of arrival** – an integer from 0 to 23.
- The fourth line contains **minutes of arrival** – an integer from 0 to 59.

### Output Data

Print the following on the first line on the console:

- "**Late**", if the student arrives **later** compared to the exam starting time.
- "**On time**", if the student arrives **exactly** at the exam starting time or up to 30 minutes earlier.
- "**Early**", if the student arrives more than 30 minutes **before** the exam starting time.

If the student arrives with more than one minute difference compared to the exam starting time, print on the next line:

- "**mm minutes before the start**" for arriving less than an hour earlier.
- "**hh:mm hours before the start**" for arriving 1 hour or earlier. Always print minutes using 2 digits, for example "1:05".
- "**mm minutes after the start**" for arriving more than an hour late.
- "**hh:mm hours after the start**" for arriving late with 1 hour or more. Always print minutes using 2 digits, for example "1:03".
- 
### Sample Input and Output

| Input | Output | Input | Output |
|---|---|---|---|
|9<br>30<br>9<br>50|Late<br>20 minutes after the start|16<br>00<br>15<br>00|Early<br>1:00 hours before the start|
|9<br>00<br>8<br>30|On time<br>30 minutes before the start|9<br>00<br>10<br>30|Late<br>1:30 hours after the start|
|14<br>00<br>13<br>55|On time<br>5 minutes before the start|11<br>30<br>8<br>12|Early<br>3:18 hours before the start|


| Input | Output | 
|---|---|
|10<br>00<br>10<br>00|On time|
|11<br>30<br>10<br>55|Early<br>35 minutes before the start|
|11<br>30<br>12<br>29|Late<br>59 minutes after the start|

### Hints and Guidelines

<table><tr><td><img src="/assets/alert-icon.png" style="max-width:50px" /></td>
<td>It is recommended <strong>to read the assignment a few times,</strong> take notes and sketch the examples while thinking before you start with the code.</td></tr></table>

#### Processing the Input Data

According to the assignment, we expect **four** lines containing different **integers** to be passed. Examining the provided parameters, we can use the **`int`** type, as it is suitable for the expected values. We simultaneously **read** the input data and **parse** the string value to the selected data type for the **intege**r.

![](/assets/chapter-4-2-images/01.On-time-for-the-exam-01.png)

Examining the expected output, we can create variables that contain the different output data types, to avoid using the so-called **"magic strings"** in the code.

![](/assets/chapter-4-2-images/01.On-time-for-the-exam-02.png)

#### Calculations

After reading the input data, we can now start writing the logic for calculating the result. Let's first calculate the **start time** of the exam **in minutes** for an easier and more accurate comparison:

![](/assets/chapter-4-2-images/01.On-time-for-the-exam-03.png)

Let's also calculate the **student arrival time** using the same logic:

![](/assets/chapter-4-2-images/01.On-time-for-the-exam-04.png)

What remains is to calculate the difference between the two times, to determine **when** and **what time compared to the exam time** the student arrived at:

![](/assets/chapter-4-2-images/01.On-time-for-the-exam-05.png)

Our next step is to do the required **checks and calculations**, and finally, we will print the output. Let's separate the code into **two** parts.

- First, let's show when the student arrived – were they early, late or on time. To do that, we will use an **`if-else`** statement. 
- After that, we will show the **time difference**, if the student arrives at a **different time** compared to the **exam starting time**.

To spare one additional check (**`else`**), we can, by default, assume that the student was late. 

After that, according to the condition, we will check whether the difference in times is **more than 30 minutes**. If this is true, we assume that the student is **early**.  If we do not match the first condition, we need to check if **the difference is less than or equal to zero (**`<= 0`**)**, by which we are checking the condition whether the student arrived within the range of **0 to 30 minutes** before the exam. 

In all other cases, we assume that the student **was late**, which we set as **default**, and no additional check is needed:

![](/assets/chapter-4-2-images/01.On-time-for-the-exam-06.png)

Finally, we need to understand and print **what is the time difference between exam start time and student arrival time**, as well as whether this time difference indicates the time of arrival **before or after the exam start**.

We check whether the time difference is **more than** one hour, to print hours and minutes in the required **format**, or **less than** one hour, to print **only minutes** as a format and description. We also need to do one more check – whether the time of student's arrival is **before** or **after** the exam start time.

![](/assets/chapter-4-2-images/01.On-time-for-the-exam-07.png)

#### Printing the Result

Finally, what remains is to print the result on the console. According to the requirements, if the student arrived right on time **(not even a minute difference)**, we do not need to print a second result. This is why we apply the following **condition**:

![](/assets/chapter-4-2-images/01.On-time-for-the-exam-08.png)

Actually, for the task, printing the result **on the console** can be done at a much earlier stage – during the calculations. This, however, is not a very good practice. **Why?**

Let's examine the idea that our code is not 10 lines, but 100 or 1000! One day, printing the result will not be done on the console, but will be written in a **file** or displayed as a **web application**. Then, how many places in the code you will make changes at, due to such a correction? Are you sure you won't miss some places?

<table><tr><td><img src="/assets/alert-icon.png" style="max-width:50px" /></td>
<td>Always consider the code that contains logical calculations as a separate part, different from the part that processes the input and output data. It has to be able to work regardless of how the data is passed to it and where the result will be displayed.</td></tr></table>

### Testing in the Judge System

Test your solution here:  [https://judge.softuni.org/Contests/Practice/Index/1052#0](https://judge.softuni.org/Contests/Practice/Index/1052#0).


## Problem: Trip

It is strange, but most people start planning their vacations well in advance. A young programmer from Bulgaria has a **certain budget** and spare time in a particular **season**.

Write a program that accepts **as input the budget and season** and **as output** displays programmer's **vacation place** and **the amount of money they will spend**.

**The budget determines the destination, and the season determines what amount of the budget will be spent**. If the season is summer, the programmer will go camping, if it is winter – he will stay in a hotel. If it is in Europe, regardless of the season, the programmer will stay in a hotel. Each camp or hotel, according to the destination, has its price, which corresponds to a particular **percentage of the budget**:

- If **100 BGN or less** – somewhere in **Bulgaria**.
  - **Summer** – **30%** of the budget
  - **Winter** – **70%** of the budget.
- If **1000 BGN or less** – somewhere in the **Balkans**.
  - **Summer** – **40%** of the budget.
  - **Winter** – **80%** of the budget.
- If **more than 1000 BGN** – somewhere in **Europe**.
  - Upon traveling in Europe, regardless of the season, the programmer will spend **90% of the budget**.
  
### Input Data

The input data will be read from the console and will consist of **two lines**:

- The **first** line holds **the budget** – a **real number** in the range [**10.00 … 5000.00**].
- The **second** line holds one of two possible seasons that are "**summer**" or "**winter**".
- 
### Output Data

**Two lines** must be printed on the console.

- On the **first** line – "**Somewhere in {destination}**" among "**Bulgaria**", "**Balkans**" and "**Europe**".
- On the **second** line – "{**Vacation type**} – {**Amount spent**}".
  - The **Vacation** can be in a "**Camp**" or "**Hotel**".
  - The **Amount** must be **rounded up to the second digit after the decimal point**.

### Sample Input and Output

| Input | Output |
|---|---|
|50<br>summer|Somewhere in Bulgaria<br>Camp - 15.00|
|75<br>winter|Somewhere in Bulgaria<br>Hotel - 52.50|
|312<br>summer|Somewhere in Balkans<br>Camp - 124.80|
|678.53<br>winter|Somewhere in Balkans<br>Hotel - 542.82|
|1500<br>summer|Somewhere in Europe<br>Hotel - 1350.00|

### Hints and Guidelines

Typically, as for the other tasks, we can separate the solution into the following parts:
* Reading the input data
* Doing calculations
* Printing the result

#### Обработка на входните данни

While reading carefully the requirements, we understand that we expect **two** lines of input data. Our first parameter is a **real number**, for which we need to pick an appropriate variable type. Ще се спрем на **`float`** като тип за бюджета, а за сезона - **`string`**: 

![](/assets/chapter-4-2-images/02.Trip-01.png)

<table><tr><td><img src="/assets/alert-icon.png" style="max-width:50px" /></td>
<td>Винаги преценявайте какъв <strong>тип стойност</strong> се подава при входните данни, както и към какъв тип трябва да бъдат конвертирани тези данни, за да работят правилно създадените от вас програмни конструкции!</td>
</tr></table>

#### Изчисления

Нека си създадем и инициализираме нужните за логиката и изчисленията променливи:

![](/assets/chapter-4-2-images/02.Trip-02.png)

Подобно на примера в предната задача, можем да инициализираме променливите с някои от изходните резултати - с цел спестяване на допълнително инициализиране.

Разглеждайки отново условието на задачата забелязваме, че основното разпределение за това къде ще почиваме се определя от **стойността на подадения бюджет**, т.е. основната ни логика се разделя на два случая: 
* Ако бюджетът е **по-малък** от дадена стойност.
* Ако е **по-малък** от друга стойност, или е **повече** от дадена гранична стойност. 

Спрямо това как си подредим логическата схема (в какъв ред ще обхождаме граничните стойности), ще имаме повече или по-малко проверки в условията. **Помислете защо!**

След това е необходимо да направим проверка за стойността на **подадения сезон**. Спрямо нея ще определим какъв процент от бюджета ще бъде похарчен, както и къде ще почива програмистът - в **хотел** или на **къмпинг**. Пример за един от възможните подходи за решение е:

![](/assets/chapter-4-2-images/02.Trip-03.png)

Винаги можем да инициализираме дадена стойност на параметъра и след това да направим само една проверка. **Това ни спестява една логическа стъпка**. Например следният блок:

![](/assets/chapter-4-2-images/02.Trip-04.png)

може да бъде съкратен до този си вид:

![](/assets/chapter-4-2-images/02.Trip-05.png)

#### Отпечатване на резултата

Остава ни да покажем изчисления резултат на конзолата:

![](/assets/chapter-4-2-images/02.Trip-06.png)

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.org/Contests/Practice/Index/1052#1](https://judge.softuni.org/Contests/Practice/Index/1052#1).


## Задача: операции между числа

Напишете програма, която чете **две цели числа (n1 и n2)** и **оператор**, с който да се извърши дадена математическа операция с тях. Възможните операции са: **събиране** (**`+`**), **изваждане** (**`-`**), **умножение** (**`*`**), **деление** (**`/`**) и **модулно деление** (**`%`**). При събиране, изваждане и умножение на конзолата трябва да се отпечата резултата и дали той е **четен** или **нечетен**. При обикновено деление – **единствено резултата**, а при модулно деление – **остатъка**. Трябва да се има предвид, че **делителят може да е равен на нула** (**`= 0`**), а на нула не се дели. В този случай трябва да се отпечата **специално съобщение**.

### Входни данни

От конзолата се прочитат **3 реда**:

- **N1** – **цяло число** в интервала [**0 … 40 000**].
- **N2** – **цяло число** в интервала [**0 … 40 000**].
- **Оператор** – **един символ** измежду: "**+**", "**-**", "**\***", "**/**", "**%**".

### Изходни данни

Да се отпечата на конзолата **един ред**:

- Ако операцията е **събиране**, **изваждане** или **умножение**:
  - **"{N1} {оператор} {N2} = {резултат} – {even/odd}"**.
- Ако операцията е **деление**:
  - **"{N1} / {N2} = {резултат}"** – резултатът е **форматиран** до **втория символ след десетичния знак**.
- Ако операцията е **модулно деление**:
  - **"{N1} % {N2} = {остатък}"**.
- В случай на **деление на 0** (нула):
  - **"Cannot divide {N1} by zero"**.

### Примерен вход и изход

| Вход | Изход | Вход | Изход |
|---|---|---|---|
|123<br>12<br>/|123 / 12 = 10.25|112<br>0<br>/|Cannot divide 112 by zero|
|10<br>3<br>%|10 % 3 = 1|10<br>0<br>%|Cannot divide 10 by zero|

| Вход | Изход |
|---|---|
|10<br>12<br>+|10 + 12 = 22 - even|
|10<br>1<br>-|10 - 1 = 9 - odd|
|7<br>3<br>\*|7 * 3 = 21 - odd|

### Насоки и подсказки

Задачата не е сложна, но има доста редове код за писане.

#### Обработка на входните данни

След прочитане на условието разбираме, че очакваме три реда с входни данни. На първите **два** реда ни се подават **цели числа** (в указания от заданието диапазон), а на третия - **аритметичен символ**: 

![](/assets/chapter-4-2-images/03.Operations-01.png)

#### Изчисления

Нека си създадем и инициализираме нужните за логиката и изчисленията променливи. В едната ще пазим **резултата от изчисленията**, а другата ще използваме за **крайния изход** на програмата:

![](/assets/chapter-4-2-images/03.Operations-02.png)

Прочитайки внимателно условието разбираме, че има случаи, в които не трябва да правим **никакви** изчисления, а просто да изведем резултат. Следователно първо може да проверим дали второто число е **`0`** (нула), както и дали операцията е **деление** или **модулно деление**, след което да инициализираме резултата:

![](/assets/chapter-4-2-images/03.Operations-03.png)

Нека сложим резултата като стойност при инициализацията на **`output`** параметъра. По този начин може да направим само **една проверка** - дали е необходимо да **преизчислим** и **заменим** този резултат. 

Спрямо това кой подход изберем, следващата ни проверка ще бъде или обикновен **`elif`** или единичен **`if`**. В тялото на тази проверка, с допълнителни проверки за начина на изчисление на резултата спрямо подадения оператор, можем да разделим логиката спрямо **структурата** на очаквания **резултат**. 

От условието можем да видим, че за **събиране** (**`+`**), **изваждане** (**`-`**) или **умножение** (**`*`**) очакваният резултат има еднаква структура: **"{n1} {оператор} {n2} = {резултат} – {even/odd}"**, докато за **деление** (**`/`**) и за **модулно деление** (**`%`**) резултатът има различна структура:

![](/assets/chapter-4-2-images/03.Operations-04.png)

Завършваме с проверките за събиране, изваждане и умножение:

![](/assets/chapter-4-2-images/03.Operations-05.png)

При кратки и ясни проверки, както в горния пример за четно и нечетно число, е възможно да се използва **тернарен оператор**, който просто спестява няколко реда код. Нека разгледаме възможната проверка **с** и **без** тернарен оператор.

**Без използване на тернарен оператор** кодът е по-дълъг, но се чете лесно:

![](/assets/chapter-4-2-images/03.Operations-06.png)

**С използване на тернарен оператор** кодът е много по-кратък, но може да изисква допълнителни усилия, за да бъде прочетен и разбран като логика:

![](/assets/chapter-4-2-images/03.Operations-07.png)

#### Отпечатване на резултата

Накрая ни остава да покажем изчисления резултат на конзолата:

![](/assets/chapter-4-2-images/03.Operations-08.png)

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.org/Contests/Practice/Index/1052#2](https://judge.softuni.org/Contests/Practice/Index/1052#2).


## Задача: билети за мач

**Група запалянковци** решили да си закупят **билети за Евро 2016**. Цената на билета се определя спрямо **две** категории:

- **VIP** – **499.99** лева.
- **Normal** – **249.99** лева.

Запалянковците **имат определен бюджет**, a **броят на хората** в групата определя какъв процент от бюджета трябва **да се задели за транспорт**:

- **От 1 до 4** – 75% от бюджета.
- **От 5 до 9** – 60% от бюджета.
- **От 10 до 24** – 50% от бюджета.
- **От 25 до 49** – 40% от бюджета.
- **50 или повече** – 25% от бюджета.

Напишете програма, която да **пресмята дали с останалите пари от бюджета** могат да си **купят билети за избраната категория**, както и колко пари ще им **останат или ще са им нужни**.

### Входни данни

Входът се чете от **конзолата** и съдържа **точно 3 реда**:

- На **първия** ред е **бюджетът** – реално число в интервала [**1 000.00 … 1 000 000.00**].
- На **втория** ред е **категорията** – "**VIP**" или "**Normal**".
- На **третия** ред е **броят на хората в групата** – цяло число в интервала [**1 … 200**].

### Изходни данни

Да се **отпечата** на конзолата **един ред**:

- Ако **бюджетът е достатъчен**:
  - "**Yes! You have {N} leva left.**" – където **N са останалите пари** на групата.
- Ако **бюджетът НЕ Е достатъчен**:
  - "**Not enough money! You need {М} leva.**" – където **М е сумата, която не достига**.

**Сумите** трябва да са **форматирани с точност до два символа след десетичния знак**.

### Примерен вход и изход

| Вход | Изход | Обяснения |
|---|---|---|
|1000<br>Normal<br>1|Yes! You have 0.01 leva left.|**1 човек : 75%** от бюджета отиват за **транспорт**.<br>**Остават:** 1000 – 750 = **250**.<br>Категория **Normal**: билетът **струва 249.99 * 1 = 249.99**<br>249.99 < 250: **остават му** 250 – 249.99 = **0.01**|

| Вход | Изход | Обяснения |
|---|---|---|
|30000<br>VIP<br>49|Not enough money! You need 6499.51 leva.|**49 човека: 40%** от бюджета отиват за **транспорт**.<br>Остават: 30000 – 12000 = 18000.<br>Категория **VIP**: билетът **струва** 499.99 * 49.<br>**24499.510000000002** < 18000.<br>**Не стигат** 24499.51 - 18000 = **6499.51**|

### Насоки и подсказки

Ще прочетем входните данни и ще извършим изчисленията, описани в условието на задачата, за да проверим дали ще стигнат парите.

#### Обработка на входните данни

Нека прочетем внимателно условието и да разгледаме какво се очаква да получим като **входни данни**, какво се очаква да **върнем като резултат**, както и кои са **основните стъпки** при разбиването **на логическата схема**. Като за начало, нека обработим и запазим входните данни в **подходящи** за това **променливи**:

![](/assets/chapter-4-2-images/04.Match-tickets-01.png)

#### Изчисления

Нека създадем и инициализираме нужните за изчисленията променливи:

![](/assets/chapter-4-2-images/04.Match-tickets-02.png)

Нека отново прегледаме условието. Трябва да направим **две** различни блок изчисления. От първите изчисления трябва да разберем каква част от бюджета ще трябва да заделим за **транспорт**. За логиката на тези изчисления забелязваме, че има значение единствено **броят на хората в групата**. Следователно ще направим логическата разбивка спрямо броя на запалянковците. Ще използваме условна конструкция - поредица от **`if-elif`** блокове:

![](/assets/chapter-4-2-images/04.Match-tickets-03.png)

От вторите изчисления трябва да намерим каква сума ще ни е необходима за закупуване на **билети за групата**. Според условието, това зависи единствено от типа на билетите, които трябва да закупим. Нека използваме **`if-elif`** условна конструкция:

![](/assets/chapter-4-2-images/04.Match-tickets-04.png)

След като сме изчислили какви са **транспортните разходи** и **разходите за билети**, ни остава да изчислим крайния резултат и да разберем **ще успее** ли групата от запалянковци да отиде на Евро 2016 или **няма да успее** при така подадените параметри. 

За извеждането на резултата, за да си спестим една **проверка** в конструкцията, приемаме, че групата по подразбиране ще може да отиде на Евро 2016:

![](/assets/chapter-4-2-images/04.Match-tickets-05.png)

#### Отпечатване на резултата

Накрая ни остава да покажем изчисления резултат на конзолата.

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.org/Contests/Practice/Index/1052#3](https://judge.softuni.org/Contests/Practice/Index/1052#3).


## Задача: хотелска стая

Хотел предлага **два вида стаи**: **студио и апартамент**.

Напишете програма, която изчислява **цената за целия престой за студио и апартамент**. **Цените** зависят от **месеца** на престоя:

| **Май и октомври** | **Юни и септември** | **Юли и август** |
|---|---|---|
|Студио – **50** лв./нощувка|Студио – **75.20** лв./нощувка|Студио – **76** лв./нощувка|
|Апартамент – **65** лв./нощувка|Апартамент – **68.70** лв./нощувка|Апартамент – **77** лв./нощувка|

Предлагат се и следните **отстъпки**:

- За **студио**, при **повече** от **7** нощувки през **май и октомври**: **5% намаление**.
- За **студио**, при **повече** от **14** нощувки през **май и октомври**: **30% намаление**.
- За **студио**, при **повече** от **14** нощувки през **юни и септември**: **20% намаление**.
- За **апартамент**, при **повече** от **14** нощувки, **без значение от месеца: 10% намаление**.

### Входни данни

Входът се чете от конзолата и съдържа **точно два реда**:

- На първия ред е **месецът** – **May**, **June**, **July**, **August**, **September** или **October**.
- На втория ред е **броят на нощувките** – **цяло число в интервала** [**0 … 200**].

### Изходни данни

Да се **отпечатат** на конзолата два реда:

- На първия ред: "**Apartment: { цена за целият престой } lv**".
- На втория ред: "**Studio: { цена за целият престой } lv**".

**Цената за целия престой да е форматирана с точност до два символа след десетичния знак**.

### Примерен вход и изход

| Вход | Изход |Обяснения |
|---|---|---|
|May<br>15|Apartment: 877.50 lv.<br>Studio: 525.00 lv.| През **май**, при повече от **14 нощувки**, намаляваме цената на **студиото с 30%** (50 – 15 = 35), а на **апартамента – с 10%** (65 – 6.5 =58.5).<br>Целият престой в **апартамент – 877.50** лв.<br>Целият престой **в студио – 525.00** лв.|

| Вход | Изход |
|---|---|
|June<br>14|Apartment: 961.80 lv.<br>Studio: 1052.80 lv|
|August<br>20|Apartment: 1386.00 lv.<br>Studio: 1520.00 lv.|

### Насоки и подсказки

Ще прочетем входните данни и ще извършим изчисленията според описания ценоразпис и правилата за отстъпките и накрая ще отпечатаме резултата.

#### Обработка на входните данни

Съгласно условието на задачата очакваме да получим два реда входни данни - на първия ред **месеца, през който се планува престой**, а на втория - **броя нощувки**. Нека обработим и запазим входните данни в подходящи за това променливи:

![](/assets/chapter-4-2-images/05.Hotel-room-01.png)

#### Изчисления

След това да създадем и инициализираме нужните за изчисленията променливи:

![](/assets/chapter-4-2-images/05.Hotel-room-02.png)

Разглеждайки отново условието забелязваме, че основната ни логика зависи от това какъв **месец** ни се подава, както и от броя на **нощувките**.

Като цяло има различни подходи и начини да се направят въпросните проверки, но нека се спрем на основна условна конструкция **`if-elif`**, като в различните **случаи** ще използваме съответно вложени условни конструкции **`if`** и **`if-elif`**.

Нека започнем с първата група месеци: **Май** и **Октомври**. За тези два месеца **цената на престой е еднаква** и за двата типа настаняване - в **студио** и в **апартамент**. Съответно остава само да направим вътрешна проверка спрямо **броят нощувки**, за да преизчислим **съответната цена** (ако се налага):

![](/assets/chapter-4-2-images/05.Hotel-room-03.png)

За следващите месеци **логиката** и **изчисленията** ще са донякъде **идентични**: 

![](/assets/chapter-4-2-images/05.Hotel-room-04.png)

![](/assets/chapter-4-2-images/05.Hotel-room-05.png)

След като изчислихме какви са съответните цени и крайната сума за престоя - нека да си изведем във форматиран вид резултата, като преди това го запишем в изходните ни **променливи** - **`studio_info`** и **`apartment_info`**:

![](/assets/chapter-4-2-images/05.Hotel-room-06.png)

За изчисленията на изходните параметри използваме **форматирането** **`.2f`**. Този начин на форматиране **закръгля десетично** число до **зададен брой цифри** (в случая 2) след десетичния знак, а на целите числа просто добавя необходимия брой символи след десетичната запетая.

#### Отпечатване на резултата

Накрая остава да покажем изчислените резултати на конзолата.

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.org/Contests/Practice/Index/1052#4](https://judge.softuni.org/Contests/Practice/Index/1052#4).