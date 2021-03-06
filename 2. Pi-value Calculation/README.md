## Лабораторная работа по курсу "Высокопроизводительные вычисления".<br/>
### *Расчет числа "Пи", с применением технологии CUDA.* <br/>
Samara University <br/>
HPC-2021

## 2. [Pi-value Calculation](https://github.com/Dark-MonkGI/Laboratory-work/blob/a6546ab423094863b0c75c3523074bba8c0adc50/2.%20Pi-value%20Calculation/Pi-value%20Calculation_ILia.ipynb)

**Задача:**  ([task sheet](https://github.com/Dark-MonkGI/Laboratory-work/blob/bafbfd483324ca251402b1dfc29284cf6f80fd7f/2.%20Pi-value%20Calculation/pi_monte_carlo.pdf))  Учитывая количество точек N, сгенерируйте случайное распределение в области (0, 0) - (1, 1) и вычислите число π
используя CPU и GPU. Полученные значения π должны быть распечатаны вместе со временем выполнения.<br/>
> **Task definition** <br/>
> Given the number of points N , generate a random distribution in (0, 0) − (1, 1) area and calculate the π number
>using CPU and GPU. The resulting π values should be printed out along with the execution times.<br/>

**Входные данные:** <br/>
- N - количество баллов;<br/>

**Выходные данные:** <br/>
- время выполнения программ GPU и CPU;<br/>
- Значения π, рассчитанные программами GPU и CPU (результаты могут отличаться);<br/>

Отчет о проделанной лабораторной работе - это git-репозиторий с исходным кодом.<br/>
**Язык:**  C++ или Python <br/> 

###  **Техническое обеспечение** <br/>
-  Процессор: `Intel(R) Xeon(R) CPU @ 2.30GHz`<br/>
-  Графический процессор: `b'Tesla K80'` <br/>
-  Google Colaboratory <br/>
   compute capability: 3.7 <br/>
   
###  **Описание реализации** 

Существует много способов вычисления числа Пи. Самым простым и понятным является численный метод Монте-Карло,<br/>
суть которого сводится к простейшему перебору точек на площади.<br/>
Расчет заключается в том, что бы взять квадрат со стороной a = 2 R, вписать в него круг радиусом R. И наугад ставить точки внутри квадрата.<br/>
Геометрически, вероятность P1 того, чтот точка попадет в круг, равна отношению площадей круга и квадрата:<br/>

   `P1=Sкруг / Sквадрата = πR2 / a 2 = πR2 / (2 R ) 2= πR2 / (2 R) 2 = π / 4 (1)`

Наглядное представление:<br/>
![logo](https://habrastorage.org/getpro/habr/post_images/011/ef8/989/011ef8989001df204b33142805371d9b.gif)
> Monte Carlo method applied to approximating the value of π.

Вероятность попадания точки в круг можно также посчитать после численного эксперимента ещё проще - посчитать количество точек, попавших в круг и поделить их на общее количество поставленных точек:
P2= N-попавших в круг / N-точек;
Так, при большом количестве точек в численном эксперименте вероятности должны вести себя cледующим образом:
lim(Nточек→∞)⁡(P2-P1)=0;
Следовательно:
π / 4 = Nпопавших в круг / Nточек;
π = 4 Nпопавших в круг / Nточек; 

##  **Результаты вычислений** <br/>
> Число Пи – математическая константа, которая выражает отношение длины окружности к её диаметру.<br/>
> Равна приблизительно `3,141592653589793238462643`<br/>

В таблице приведены результаты времени вычисления и получившееся число π, на CPU и GPU соответственно:  
 	 № |Device|Time(second)| Number_Pi | 
:-----:|:-----:|:-----:|:-----:|
0 | CPU |	0.44 |	3.1379|
1 | GPU |	0.21 |	3.1552|
2 | CPU |	0.82 |	3.1420375|
3 | GPU |	0.01 |	3.1578|
4 | CPU |	1.2  |   3.139591666|
5 | GPU |	0.01 |	3.1508|
6 | CPU |	1.62 |	3.14519375|
7 | GPU |   0.01 |	3.1471|
8 | CPU |	1.97 |	3.139025|
9 | GPU |	0.02 |	3.14304|
10| CPU |	2.4  |	3.1442708333|
11| GPU |	0.02 |	3.14706666|
12| CPU |	2.82 |	3.1418107142857146|
13| GPU |	0.02 |	3.147542857142857|
14| CPU |	3.24 |	3.1419750000|
15| GPU |	0.02 |	3.14745|
16| CPU |	3.6  |	3.140125|
17| GPU |	0.03 |	3.1453777|
18| CPU |	4.06 |	3.141845|
19| GPU |	0.03 |	3.14372|

<br/> 

 ##  **Вывод**<br/> 
Итог выполнения лабораторной работы - реализован алгоритм вычисления числа "Пи" по методу Монте-Карло, на CPU и GPU.
Работа выполнена на языке Python, с применением библиотека numba для задействования GPU Device.
Точность вычислений сопоставима и близка к истине, но на GPU заметно быстрее.


    
    
