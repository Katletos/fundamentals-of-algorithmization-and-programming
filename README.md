# Сортировка выбором
## Алгоритм сортировки
* находим номер минимального значения в текущем списке
* производим обмен этого значения со значением первой неотсортированной позиции (обмен не нужен, если минимальный элемент уже находится на данной позиции)
* теперь сортируем хвост списка, исключив из рассмотрения уже отсортированные элементы

## Сортировка выбором :: Selection sort

![SelectionSort](https://user-images.githubusercontent.com/40485432/138320601-43995e73-5a06-4a72-9522-45c8218a1504.gif)

Просто и незатейливо — проходим по массиву в поисках максимального элемента. Найденный максимум меняем местами с последним элементом. Неотсортированная часть массива уменьшилась на один элемент (не включает последний элемент, куда мы переставили найденный максимум). К этой неотсортированной части применяем те же действия — находим максимум и ставим его на последнее место в неотсортированной части массива. И так продолжаем до тех пор, пока неотсортированная часть массива не уменьшится до одного элемента.

Сортировка простым выбором представляет из себя грубый двойной перебор. Можно ли её улучшить? Разберём несколько модификаций.

## Двухсторонняя сортировка выбором :: Double selection sort

![DoubleSelectionSort](https://user-images.githubusercontent.com/40485432/138320623-b37b37ea-9b64-4eb8-ab3e-d3e81add37ba.gif)

Похожая идея используется в шейкерной сортировке, которая является вариантом пузырьковой сортировки. Проходя по неотсортированной части массива, мы кроме максимума также попутно находим и минимум. Минимум ставим на первое место, максимум на последнее. Таким образом, неотсортированная часть при каждой итерации уменьшается сразу на два элемента.

На первый взгляд кажется, что это ускоряет алгоритм в 2 раза — после каждого прохода неотсортированный подмассив уменьшается не с одной, а сразу с двух сторон. Но при этом в 2 раза увеличилось количество сравнений, а число свопов осталось неизменным. Двойной выбор лишь незначительно увеличивает скорость алгоритма, а на некоторых языках даже почему-то работает медленнее.
