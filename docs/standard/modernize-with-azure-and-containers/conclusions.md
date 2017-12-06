---
title: "Выводы"
description: "Модернизировать существующие приложения .NET с облако Azure и контейнеров Windows | выводы"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 0bcc330a5970ab923b48d8790c4de93171283d94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="conclusions"></a>Выводы

-   Решения на основе контейнера в конечном счете обеспечивают сокращение экономии затрат. Контейнеры являются решения проблем развертывания, так как они удаляют трения, причиной отсутствия зависимостей в производственных средах. При удалении таких проблем, его разработки и тестирования, DevOps и производственных операций значительно повышается.

-   Контейнер Docker становится стандартной единицей развертывания для любого серверного приложения или службы.

-   В рабочей среде следует использовать orchestrator (например, Service Fabric или Kubernetes) для размещения масштабируемых приложений на основе контейнеров Windows.

-   Размещение контейнеры виртуальных машинах Azure — это быстрый и простой способ создания небольших сред разработки и тестирования в облаке.

-   Экземпляр управляемого базы данных Azure SQL по умолчанию рекомендуется использовать при миграции реляционных базах данных с существующие приложения в Azure.

-   Visual Studio 2017 г. и Image2Docker являются основные средства начать модернизация существующие приложения .NET с помощью контейнеров Windows по ускорению началу работы обучения.

-   При размещении приложений в контейнерах в рабочей среде необходимо всегда создавать или внедрить средства DevOps для элемента конфигурации/CD конвейеров, например Visual Studio Team Services или Jenkins DevOps язык и региональные параметры.

-   Microsoft Azure предоставляет наиболее полные и завершения среды модернизировать существующие приложения .NET Framework с контейнерами Windows, облачной инфраструктуры и служб PaaS.

>[!div class="step-by-step"]
[Назад](walkthroughs-technical-get-started-overview.md)