## Лабораторная работа по курсу "Высокопроизводительные вычисления".<br/>
### *Реализация двустороннего фильтра, с применением технологии CUDA.* <br/>
Samara University <br/>
HPC-2021

## 3. [Bilateral filter](https://github.com/Dark-MonkGI/Laboratory-work/blob/main/3.%20Bilateral%20filter/Bilateral%20filter_ILia.ipynb)

**Задача:**  ([task sheet](https://github.com/Dark-MonkGI/Laboratory-work/blob/main/3.%20Bilateral%20filter/Methodical%20instructions%20bilateral.pdf))  
Учитывая размер изображения M × N, реализуйте и примените версию CUDA 9-точечного двустороннего фильтра и сохраните
результат в выходное изображение. Пропущенные значения в граничных строках и столбцах необходимо брать из ближайших пикселей.<br/>

> **Task definition** <br/>
> Given the image of size M×N, implement and apply a CUDA version of 9-point bilateral filter and store the
> result to output image. Missing values for edge rows and columns are to be taken from nearest pixels. CUDA implementation must make use of texture memory.<br/>


**Входные данные:** <br/>
- Входное изображение в градациях серого в формате BMP, σ values;<br/>

![logo](https://raw.githubusercontent.com/Dark-MonkGI/Laboratory-work/main/3.%20Bilateral%20filter/image/original_image_batman.bmp) <br/>

**Выходные данные:** <br/>
- Время обработки изображения с помощью процессора;<br/>
- Время обработки изображения с использованием графического процессора;<br/>
- Полученные изображения в формате BMP;<br/>

Отчет о проделанной лабораторной работе - это git-репозиторий с исходным кодом.<br/>
**Язык:**  C++ или Python <br/> 

###  **Техническое обеспечение** <br/>
-  Процессор: `Intel(R) Xeon(R) CPU @ 2.30GHz`<br/>
-  Графический процессор: `b'Tesla K80'` <br/>
-  Google Colaboratory <br/>
   compute capability: 3.7 <br/>
   
###  **Описание реализации** 
Что такое двусторонняя фильтрация?
> «Билатеральный фильтр — это нелинейный сглаживающий фильтр для изображений, сохраняющий границы и уменьшающий шум. Он заменяет интенсивность каждого пикселя средневзвешенным  значением интенсивности ближайших пикселей». <br/>

Основная идея этой математики двусторонней фильтрации заключается в том, что: <br/>

 1. Каждый пиксель заменяется средневзвешенным значением его соседей. <br/>
 2. Каждый сосед "взвешивается" с помощью пространственного компонента, который смазывает удаленные пиксели и компонента диапазона, который смазывает пиксели с разной интенсивностью. <br/>
 3. Комбинация обоих компонентов гарантирует, что в конечный результат будут вносить вклад только близкие похожие пиксели. <br/>

##  **Результаты вычислений** <br/>
Время выполнения: <br/>
№ |Device|Time(second)| 
:-----:|:-----:|:-----:|
0 | CPU |	0.0192 |
1 | GPU |	0.0056 |
<br/>

Изображение полученное при вычислении на CPU: <br/>
![logo](https://raw.githubusercontent.com/Dark-MonkGI/Laboratory-work/main/3.%20Bilateral%20filter/image/bilateral_image_on_CPU.bmp) <br/>

Изображение полученное при вычислении на GPU: <br/>
![logo](https://raw.githubusercontent.com/Dark-MonkGI/Laboratory-work/main/3.%20Bilateral%20filter/image/bilateral_image_on_GPU.bmp) <br/>

 ##  **Вывод**<br/> 
Итог выполнения лабораторной работы - реализован и применен алгоритм 9-точечного двустороннего фильтра CUDA.
Работа выполнена на языке Python, с применением библиотека numba для задействования GPU Device.
Даже с учетом не большой энергозатратности на выполнение данной операции, есть заметный прирост производительности.
Результаты вычислений визуально схожи, имеются незначительные различия контрастности, в результате различных подходов реализации данного метода.





