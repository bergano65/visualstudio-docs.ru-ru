---
title: Развертывание ClickOnce в Windows Vista | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e25f9da960b1de8acb1950b2bdd3ab7e61409f17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675466"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Развертывание ClickOnce в Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Создание приложений в Visual Studio для контроля учетных записей (UAC) в Windows Vista обычно создает внедренный манифест, закодированный как двоичные XML-данные в исполняемом файле приложения. Поскольку ClickOnce и COM-приложения без регистрации нуждаются в внешнем манифесте, Visual Studio создает файл для этих типов проектов, содержащих данные контроля учетных записей, а не внедренный манифест. По умолчанию Visual Studio использует сведения из файла с именем App. manifest для создания внешних данных манифеста контроля учетных записей (для ClickOnce и без регистрации) или для внедрения в исполняемый файл приложения (во всех остальных случаях). Visual Studio предоставляет следующие возможности для создания манифеста:  
  
- Используйте внедренный манифест. Внедрение данных контроля учетных записей в исполняемый файл приложения и запуск от имени обычного пользователя.  
  
   Это значение по умолчанию (если не используется технология ClickOnce). Этот параметр будет поддерживать обычный способ работы Visual Studio в Windows Vista; то есть создание внутреннего и внешнего манифеста с помощью `AsInvoker` .  
  
- Используйте внешний манифест. Создание внешнего манифеста с помощью App. manifest.  
  
   При этом создается только внешний манифест с использованием сведений в файле App. manifest. При публикации приложения с помощью ClickOnce или COM без регистрации Visual Studio добавляет в проект App. manifest и добавляет этот параметр.  
  
- Не использовать манифест. Создайте приложение без манифеста.  
  
   Этот подход также известен как *виртуализация*. Используйте этот параметр для совместимости с существующими приложениями из более ранних версий Visual Studio.  
  
  Новые свойства доступны на странице **приложение** конструктора проектов (только для проектов Visual C#) и в формате файла проекта MSBuild.  
  
  Обратите внимание, что метод настройки создания манифеста UAC в интегрированной среде разработки Visual Studio зависит от типа проекта (Visual C# и Visual Basic).  
  
  Сведения о настройке проектов Visual C# для создания манифеста см. в разделе [Страница "приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Сведения о настройке проектов Visual Basic для создания манифеста см. в разделе [Страница "приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>См. также:  
 [Безопасность и развертывание ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Разрешения пользователей и Visual Studio](https://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Страница "приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
