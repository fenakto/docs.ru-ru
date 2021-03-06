---
title: "Группировка результатов запросов"
description: "Сведения о группировке результатов."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: ca68cf96a2c27bbd1999d5445c14fc93e8e2566c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="group-query-results"></a>Группировка результатов запросов

Группирование — одна из самых эффективных функций LINQ. В приведенных ниже примерах демонстрируются различные способы группирования данных:  
  
-   по отдельному свойству;  
  
-   по первой букве строкового свойства;  
  
-   по расчетному числовому диапазону;  
  
-   по логическому предикату или другому выражению;  
  
-   по составному ключу.  
  
 Кроме того, два последних запроса передают свои результаты в новый анонимный тип, содержащий только имя и фамилию студента. Дополнительные сведения см. в разделе [Предложение group](../language-reference/keywords/group-clause.md).  
  
## <a name="example"></a>Пример  
 Во всех примерах в этом разделе используются указанные ниже вспомогательные классы и источники данных.  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a>Пример  
 В этом примере показана группировка элементов источника с помощью отдельного свойства элемента в качестве ключа группы. В данном случае в качестве ключа используется `string`, фамилия учащегося. Для ключа можно также использовать подстроку. При операции группирования используется компаратор проверки на равенство, используемый по умолчанию для данного типа.  
  
 Вставьте приведенный ниже метод в класс `StudentClass`. Измените оператор вызова в методе `Main` на `sc.GroupBySingleProperty()`.  
  
 [!code-csharp[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a>Пример  
 В этом примере показана группировка элементов источника, когда в качестве ключа группы используется не свойство объекта. В данном случае в качестве ключа используется первая буква фамилии учащегося.  
  
 Вставьте приведенный ниже метод в класс `StudentClass`. Измените оператор вызова в методе `Main` на `sc.GroupBySubstring()`.  
  
 [!code-csharp[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a>Пример  
 В этом примере показана группировка элементов источника путем использования числового диапазона в качестве ключа группы. Затем запрос передает результаты в анонимный тип, содержащий только имя и фамилию, а также диапазон процентилей, к которому принадлежит студент. Использование анонимного типа объясняется тем, что для отображения результатов не требуется использовать полный объект `Student`. `GetPercentile` — это вспомогательная функция, которая вычисляет процент на основе средних результатов учащегося. Метод возвращает целое число в диапазоне от 0 до 10.  
  
 [!code-csharp[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 Вставьте приведенный ниже метод в класс `StudentClass`. Измените оператор вызова в методе `Main` на `sc.GroupByRange()`.  
  
 [!code-csharp[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a>Пример  
 В этом примере показана группировка элементов источника с помощью выражения логического сравнения. В этом случае логическое выражение проверяет, превосходит ли среднее значение экзаменационного результата учащегося 75 баллов. Как и в предыдущих примерах, результаты передаются в анонимный тип, так как весь элемент источника не требуется. Обратите внимание на то, что свойства в анонимном типе становятся свойствами в члене `Key`, а при выполнении запроса доступ к ним можно получить по имени.  
  
 Вставьте приведенный ниже метод в класс `StudentClass`. Измените оператор вызова в методе `Main` на `sc.GroupByBoolean()`.  
  
 [!code-csharp[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a>Пример  
 В этом примере показано, как использовать анонимный тип для инкапсуляции ключа, содержащего несколько значений. В данном случае в качестве первого значения ключа используется первая буква фамилии учащегося. Второе значение ключа является логическим и указывает, набрал ли учащийся более 85 баллов на первом экзамене. Группы можно сортировать по любому из свойств в ключе.  
  
 Вставьте приведенный ниже метод в класс `StudentClass`. Измените оператор вызова в методе `Main` на `sc.GroupByCompositeKey()`.  
  
 [!code-csharp[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.IGrouping%602>  
 [Выражения запросов LINQ](index.md)  
 [предложение group](../language-reference/keywords/group-clause.md)  
 [Анонимные типы](../programming-guide/classes-and-structs/anonymous-types.md)  
 [Выполнить вложенный запрос в операции группирования](perform-a-subquery-on-a-grouping-operation.md)  
 [Создание вложенной группы](create-a-nested-group.md)  
 [Группировка данных](../programming-guide/concepts/linq/grouping-data.md)
