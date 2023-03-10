# Diagnosing_breast_cancer

Датасет для работы: https://www.kaggle.com/uciml/breast-cancer-wisconsin-data

Это сведения о пациентах со злокачественными и доброкачественными опухолями молочной железы.

## Задача: предсказать, какой диагноз имеет пациент. Это задача классификации — отнесения объекта к какой-либо категории.

Диагноз — это в какой-то степени категория, к которой мы относим случай. При этом значение точно, без промежуточных вариантов. 
Опухоль или доброкачественная, или злокачественная.

В качестве инструмента для работы с категориальными переменными - использование логистической регрессии и метод k-ближайших соседей. 

## Логистическая регрессия 
- модель, которая выдает вероятность соответствия той или иной категории. Это один из статистических методов классификации с использованием линейного дискриминанта Фишера. 
Она входит в топ часто используемых алгоритмов при исследовании данных.

Значением функции является вероятность того, что данное исходное значение принадлежит к определенному классу. 
Представим, что у нас есть какое-то пространство, в котором в виде точек размещены наши исходные значения. 
Мы можем поделить это пространство с помощью линейной плоскости на подпространства, в которых будут близкие значения, наиболее вероятно принадлежащие одному классу 
(типу, категории). 
Уже упомянутый линейный дискриминант Фишера определяет направления, проекции на которые лучше всего разделят классы. В итоге получаются разделяющие линейные плоскости.
Accuracy — это доля правильных ответов алгоритма

![1](https://medach.pro/uploads/image/url/5653/00.png)



## Метод k-ближайших соседей
- как и логистическая регрессия, решает задачу классификации. 

Он относит объекты к классу, которому принадлежит большинство из k 
его ближайших соседей в многомерном пространстве признаков. «Соседи» — это объекты, близкие к исследуемому в том или ином смысле, 
причем модель понимает это буквально: подобные наблюдения близки друг к другу, а непохожие наблюдения, наоборот, удалены друг от друга. 
Фактически, расстояние между двумя наблюдениями является критерием их различия. У каждого объекта есть несколько признаков, и предполагается, что 
если объекты близки по ключевым признакам, они совпадают и по остальным, и следовательно, принадлежат к одному классу.

Нужно импортировать класс KNeighborsClassifier, в котором реализован интересный нам метод. Количество соседей k соответствует параметру n_neighbors (по умолчанию 5, мы оставим это значение). Выбор параметра k неоднозначен. Если мы выберем значение k слишком маленьким, появляется риск, что единственным ближайшим объектом окажется «выброс», т. е. объект с неправильно определенным классом, и он приведет к неверному решению. С другой стороны, увеличение значения k повышает достоверность классификации, но границы между классами становятся менее четкими.

Проблему выбора оптимального значения параметра k называют «bias-variance tradeoff», или «компромисс между [выбросами] и дисперсией». На практике чаще всего используют k = [√𝑁]. Если есть уверенность в чистоте выборки, можно уменьшить значение k.


###  Итог: Логистическая регрессия сработала лучше: она равна 97,7 % в отличии от метода k-ближайших соседей = 94,2 %.
