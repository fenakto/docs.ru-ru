---
title: "Логическая архитектура и физическая архитектура"
description: "Архитектура Микрослужбами .NET для приложений .NET в контейнерах | Логическая архитектура и физическая архитектура"
keywords: "Docker, микрослужбы, ASP.NET, контейнер"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 635774a8fcd0cf1c0ede6a73c604071f538a37fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="logical-architecture-versus-physical-architecture"></a>Логическая архитектура и физическая архитектура

Это полезно на этом этапе для остановки и обсудить различие между логической архитектуры и физическая архитектура и как это применяется для разработки приложений на основе микрослужбу.

Чтобы начать, построение микрослужбами не требуется использовать какой-либо определенной технологии. Например контейнеры Docker не являются обязательными для создания микрослужбу-архитектурой. Также можно выполнять эти микрослужбами как обычный процессов. Микрослужбами является логической архитектуры.

Кроме того, даже если микрослужбу может быть физически реализуются как одной службы, процесса или контейнер (для простоты реализую это подходов, использованных в первоначальной версии [eShopOnContainers](http://aka.ms/MicroservicesArchitecture)), это соответствие между микрослужбу бизнеса и физической службы или контейнера не требуется обязательно во всех случаях при построении больших и сложных приложений, состоящие из многих десятки и даже сотни служб.

Это место, куда разницы между логической архитектуры и физическая архитектура приложения. Логическая архитектура и логических границ системы не обязательно полностью соответствуют архитектуре физические компьютеры или развертывания. Это может произойти, но это часто не так.

Несмотря на то, что может определения определенных микрослужбами бизнеса или ограниченных контекстах, это не означает всегда является лучшим способом, их следует реализовывать путем создания одной службы (например, веб-API ASP.NET) или один контейнер Docker для каждого микрослужбу бизнес. Наличие правило о том, каждый микрослужбу бизнеса должен быть реализован с помощью одной службы или контейнер является слишком жесткие.

Таким образом, микрослужбу бизнеса или ограниченного контекста имеет логическую архитектуру, которая может синхронизироваться (или нет) с физической архитектуры. Важно то, что микрослужбу бизнеса или ограниченного контекста должен быть автономной, позволяя код состояния меняться независимо друг от друга, развертывания и масштабирования.

Как показано на рис. 4-8, микрослужбу бизнеса каталога может состоять из нескольких служб или процессов. Это могут быть несколько служб веб-API ASP.NET или любого другого типа службы с помощью HTTP или любой другой протокол. Более того службы может делиться те же данные при условии, что эти службы являются целостного по отношению к домену бизнеса.

![](./media/image8.png)

**Рис. 4-8**. Микрослужбу бизнеса с помощью нескольких физических служб

Службы, в примере общий доступ к одной и той же модели данных, поскольку службы веб-API предназначен для тех же данных службы поиска. Таким образом в физической реализации микрослужбу бизнеса требуется разделить эти функциональные возможности, можно масштабировать каждой из них внутренней вверх или вниз при необходимости. Может быть веб-API службы обычно требуется более экземпляры службы поиска, или наоборот.)

Иными словами логической архитектуры микрослужбами не всегда имеет совпадают с архитектурой физическое развертывание. В этом руководстве каждый раз, когда мы упомянем микрослужбу означает бизнес- или логических микрослужбу, который можно сопоставить одну или несколько служб. В большинстве случаев это будет одной службы, но может быть несколько.


>[!div class="step-by-step"]
[Предыдущие] (данные независимости на microservice.md) [Далее] (распределенных, данные management.md)