---
title: "Классы (Руководство по программированию на C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: "40"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37e810fc5a5397a6b9240346ac28505b11b1e817
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="classes-c-programming-guide"></a>Классы (Руководство по программированию на C#)
*Класс* — это конструкция, которая позволяет создавать собственные настраиваемые типы путем группирования переменных других типов, методов и событий. Класс похож на проект. Он определяет данные и поведение типа. Если класс не объявлен как статический, клиентский код может использовать его, создавая *объекты* или *экземпляры*, назначенные переменной. Переменная остается в памяти до тех пор, пока все ссылки на нее не выйдут из области. В этот момент среда CLR помечает ее пригодной для сборки мусора. Если класс объявляется как [статический](../../../csharp/language-reference/keywords/static.md), то в памяти существует только одна копия, и клиентский код может получать к ней доступ только через сам класс, а не *переменную экземпляра*. Дополнительные сведения см. в разделе [Статические классы и члены статических классов](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 В отличие от структур, классы поддерживают *наследование*, фундаментальную характеристику объектно-ориентированного программирования. Дополнительные сведения см. в разделе [Наследование](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## <a name="declaring-classes"></a>Объявление классов  
 Классы объявляются с помощью ключевого слова [class](../../../csharp/language-reference/keywords/class.md), как показано в следующем примере:  
  
 [!code-csharp[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]  
  
 Ключевому слову `class` предшествует уровень доступа. Поскольку в этом случае используется открытый класс ([public](../../../csharp/language-reference/keywords/public.md)), любой пользователь может создавать объекты из этого класса. За ключевым словом `class`следует имя класса. Оставшаяся часть определения — это тело класса, в котором задаются данные и поведение. Поля, свойства, методы и события в классе собирательно называются *членами класса*.  
  
## <a name="creating-objects"></a>Создание объектов  
 Несмотря на то, что они иногда взаимозаменяемы, класс и объект — разные вещи. Класс определяет тип объекта, но не является объектом. Объект — это конкретная сущность, основанная на классе, которую иногда называют экземпляром класса.  
  
 Объекты можно создавать с помощью ключевого слова [new](../../../csharp/language-reference/keywords/new.md), за которым следует имя класса, на котором будет основан объект, например следующим образом:  
  
 [!code-csharp[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]  
  
 При создании экземпляра класса ссылка на объект передается программисту. В предыдущем примере `object1` представляет собой ссылку на объект, который основан на `Customer`. Эта ссылка указывает на новый объект, но не содержит данные этого объекта. Фактически, можно создать ссылку на объект без создания собственно объекта:  
  
 [!code-csharp[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]  
  
 Создание таких ссылок, которые не указывают на объект, не рекомендуется, так как попытка доступа к объекту по такой ссылке приведет к сбою во время выполнения. Однако такую ссылку можно сделать указывающей на объект, создав новый объект или назначив ее существующему объекту, как показано далее:  
  
 [!code-csharp[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]  
  
 В этом коде создаются две ссылки на объект, которые указывают на один и тот же объект. Таким образом, любые изменения объекта, выполненные посредством `object3`, будут отражены при последующем использовании `object4`. Поскольку на объекты, основанные на классах, указывают ссылки, классы называют ссылочными типами.  
  
## <a name="class-inheritance"></a>Наследование классов  
 При наследовании создается *производный* класс, то есть класс объявляется с помощью *базового класса*, от которого он наследует данные и поведение. Базовый класс задается добавлением после имени производного класса двоеточия и имени базового класса, как показано далее:  
  
 [!code-csharp[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]  
  
 Когда класс объявляет базовый класс, он наследует все члены базового класса, за исключением конструкторов.  
  
 В отличие от C++, класс в C# может только напрямую наследовать от одного базового класса. Тем не менее, поскольку базовый класс может сам наследовать от другого класса, класс может косвенно наследовать от нескольких базовых классов. Кроме того, класс может напрямую реализовать несколько интерфейсов. Дополнительные сведения см. в разделе [Интерфейсы](../../../csharp/programming-guide/interfaces/index.md).  
  
 Класс может быть объявлен [абстрактным](../../../csharp/language-reference/keywords/abstract.md). Абстрактный класс содержит абстрактные методы, которые имеют определение сигнатуры, но не имеют реализации. Нельзя создавать экземпляры абстрактных классов. Они могут использоваться только через производные классы, реализующие абстрактные методы. И наоборот, [запечатанный](../../../csharp/language-reference/keywords/sealed.md) класс не позволяет другим классам быть от него производными. Дополнительные сведения см. в статье [Абстрактные и запечатанные классы и члены классов](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Определения классов можно разделить между различными исходными файлами. Дополнительные сведения см. в разделе [Разделяемые классы и методы](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="description"></a>Описание  
 В следующем примере определяется открытый класс, содержащий одно поле, метод и специальный метод, вызывающий конструктор. Дополнительные сведения см. в разделе [Конструкторы](../../../csharp/programming-guide/classes-and-structs/constructors.md). Затем создается экземпляр этого класса с помощью ключевого слова `new`.  
  
## <a name="example"></a>Пример  
 [!code-csharp[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]  
  
## <a name="c-language-specification"></a>Спецификация языка C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)  
 [Объектно-ориентированное программирование](../concepts/object-oriented-programming.md)  
 [Полиморфизм](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [Члены](../../../csharp/programming-guide/classes-and-structs/members.md)  
 [Методы](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Конструкторы](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Методы завершения](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [Объекты](../../../csharp/programming-guide/classes-and-structs/objects.md)
