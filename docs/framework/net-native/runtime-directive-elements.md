---
title: "Элементы директив среды выполнения | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Элементы директив среды выполнения
Формат файла директив \(rd.xml\) среды выполнения поддерживает следующие элементы директивы среды выполнения.  Иерархическое представление см. в разделе [Ссылка на файл конфигурации директив среды выполнения \(rd.xml\)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
 [\<Application\>](../../../docs/framework/net-native/application-element-net-native.md)  
 Применяется политика отражения среды выполнения для всех типов, используемых в приложении и служит в качестве контейнера для приложения типы и члены типов, метаданные которого доступны для отражения во время выполнения.  Это дочерний элемент для элемента [\<Directives\>](../../../docs/framework/net-native/directives-element-net-native.md).  
  
 [\<Assembly\>](../../../docs/framework/net-native/assembly-element-net-native.md)  
 Применяет политику среды выполнения ко всем типам в сборке.  Это дочерний элемент элементов [\<Application\>](../../../docs/framework/net-native/application-element-net-native.md) и [\<Library\>](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<AttributeImplies\>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 Если содержащая директива [\<Type\>](../../../docs/framework/net-native/type-element-net-native.md) является атрибутом, применяет политику среды выполнения к элементам кода, к которым применяется атрибут.  
  
 [\<Directives\>](../../../docs/framework/net-native/directives-element-net-native.md)  
 Корневой элемент в любом файле директив среды выполнения для [!INCLUDE[net_native](../../../includes/net-native-md.md)].  Его дочерними элементами являются элементы [\<Application\>](../../../docs/framework/net-native/application-element-net-native.md) и [\<Library\>](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<Event\>](../../../docs/framework/net-native/event-element-net-native.md)  
 Применяет политику среды выполнения к событию.  Это дочерний элемент элементов [\<Type\>](../../../docs/framework/net-native/type-element-net-native.md) и [\<TypeInstantiation\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<Field\>](../../../docs/framework/net-native/field-element-net-native.md)  
 Применяет политику среды выполнения к полю.  Это дочерний элемент элементов [\<Type\>](../../../docs/framework/net-native/type-element-net-native.md) и [\<TypeInstantiation\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<GenericParameter\>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 Применяет политику среды выполнения к параметру типа универсального типа или метода.  
  
 [\<ImpliesType\>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 Применяет политику среды выполнения к типу, если политика была применена к содержащему типу или методу.  
  
 [\<Library\>](../../../docs/framework/net-native/library-element-net-native.md)  
 Применяет политику среды выполнения ко всем типам в сборке.  Это дочерний элемент элементов [\<Application\>](../../../docs/framework/net-native/application-element-net-native.md) и [\<Library\>](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<Method\>](../../../docs/framework/net-native/method-element-net-native.md)  
 Применяет политику среды выполнения к методу.  Это дочерний элемент элементов [\<Type\>](../../../docs/framework/net-native/type-element-net-native.md) и [\<TypeInstantiation\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<MethodInstantiation\>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 Применяет политику среды выполнения к сконструированному универсальному методу.  Это дочерний элемент элементов [\<Type\>](../../../docs/framework/net-native/type-element-net-native.md) и [\<TypeInstantiation\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<Namespace\>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 Применяет политику среды выполнения ко всем типам в пространстве имен.  
  
 [\<Parameter\>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 Применяет политику среды выполнения к типу аргумента, переданного методу.  
  
 [\<Property\>](../../../docs/framework/net-native/property-element-net-native.md)  
 Применяет политику среды выполнения к свойству.  Это дочерний элемент элементов [\<Type\>](../../../docs/framework/net-native/type-element-net-native.md) и [\<TypeInstantiation\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 [\<Subtypes\>](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 Применяет политику среды выполнения для всех классов, унаследованных из содержащего типа.  
  
 [\<Type\>](../../../docs/framework/net-native/type-element-net-native.md)  
 Применяет политику среды выполнения к типу.  
  
 [\<TypeInstantiation\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 Применяет политику среды выполнения к сконструированному универсальному типу.  
  
 [\<TypeParameter\>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 Применяет политику среды выполнения к типу, представленному аргументом <xref:System.Type>, переданным методу.  
  
## См. также  
 [Ссылка на файл конфигурации RD.XML](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)