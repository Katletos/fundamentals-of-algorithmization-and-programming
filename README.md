# Сортировка выбором
## Алгоритм сортировки
* находим номер минимального значения в текущем списке
* производим обмен этого значения со значением первой неотсортированной позиции (обмен не нужен, если минимальный элемент уже находится на данной позиции)
* теперь сортируем оставшийся список, исключив из рассмотрения уже отсортированные элементы

## Сортировка выбором :: Selection sort

<p align="center">
  <img src="https://user-images.githubusercontent.com/40485432/138336768-6fb0eff7-9eb6-4cbc-b000-b101d81bffb9.gif" />
</p>

Просто и незатейливо — проходим по массиву в поисках минимального элемента. Найденный минимум меняем местами с первым элементом. Неотсортированная часть массива уменьшилась на один элемент. К этой неотсортированной части применяем те же действия — находим минимум и ставим его на первое место в неотсортированной части массива. И так продолжаем до тех пор, пока неотсортированная часть массива не уменьшится до одного элемента.

Сортировка простым выбором представляет из себя грубый двойной перебор. Можно ли её улучшить? Разберём несколько модификаций.

## Двухсторонняя сортировка выбором :: Double selection sort

![DoubleSelectionSort](https://user-images.githubusercontent.com/40485432/138320623-b37b37ea-9b64-4eb8-ab3e-d3e81add37ba.gif)

Похожая идея используется в шейкерной сортировке, которая является вариантом пузырьковой сортировки. Проходя по неотсортированной части массива, мы кроме минимума  также попутно находим и максимума. Минимум ставим на первое место, максимум на последнее. Таким образом, неотсортированная часть при каждой итерации уменьшается сразу на два элемента.

На первый взгляд кажется, что это ускоряет алгоритм в 2 раза — после каждого прохода неотсортированный подмассив уменьшается не с одной, а сразу с двух сторон. Но при этом в 2 раза увеличилось количество сравнений, а число свопов осталось неизменным.

## Код программы на Delphi
```
program SelectionSort;

{$APPTYPE CONSOLE}
{$R *.res}

uses
  System.SysUtils;

const
  N = 10;

type
  mas = array [1 .. N] of integer;

var
  A: mas;
  i, j, min, tmp: integer;

begin
  writeln('Enter 10 values: ');
  for i := 1 to N do
  begin
    write('Element №', i, ': ');
    readln(A[i]);
  end;

  for i := 1 to N - 1 do
  begin
    min := i;

    for j := i + 1 to N do
      if A[j] < A[min] then
        min := j;

    tmp := A[i];
    A[i] := A[min];
    A[min] := tmp;
  end;

  for i := 1 to N do
  begin
    writeln('Element № ', i, ' Value: ', A[i]);
  end;

  readln;

end.
```
## Блок-схема
<p align="center">
  <img src="https://user-images.githubusercontent.com/40485432/138338618-93f107f1-ed25-458a-85ae-15ce022821b4.png"/>
</p>
