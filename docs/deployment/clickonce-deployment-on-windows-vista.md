---
title: Развертывание ClickOnce в Windows Vista | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0389665349ae9c39a0f820bc047af6cc4db2b683
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867537"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Развертывание ClickOnce в Windows Vista

Создание приложений в Visual Studio для контроля учетных записей (UAC) на Windows Vista обычно создается внедренный манифест, как двоичные данные в кодировке XML в исполняемый файл приложения.  Приложений ClickOnce и COM без регистрации требуется внешний манифест, поэтому Visual Studio создает файл для этих проектов, содержащих данные контроля учетных Записей, а не внедренный манифест. Для развертываний ClickOnce и COM без регистрации, Visual Studio использует сведения из файла с именем *app.manifest* для создания внешних контроля учетных Записей сведения о манифесте. Для всех остальных случаях Visual Studio внедряет данных контроля учетных Записей в исполняемый файл приложения. 

Visual Studio предоставляет следующие возможности для создания манифеста:  
  
- Использование внедренного манифеста. Внедрение данных UAC в исполняемый файл приложения и запуск от имени обычного пользователя.  
  
   Это параметр по умолчанию (Если вы не используете ClickOnce). Этот параметр поддерживает как обычно, в котором работает Visual Studio в Windows Vista, с созданием внутренним и внешним манифест с помощью `AsInvoker`.  
  
- Использование внешнего манифеста. Создайте внешний манифест с помощью *app.manifest*.  
  
   Это приводит к возникновению ошибки только внешний манифест, используя сведения из *app.manifest*. При публикации приложения с помощью ClickOnce или COM без регистрации, Visual Studio добавляет *app.manifest* в проект, а затем добавляет этот параметр.  
  
- Работа без использования манифеста. Создайте приложение без манифеста.  
  
   Этот подход также называется *виртуализации*. Используйте этот параметр для совместимости с существующими приложениями из более ранних версиях Visual Studio.  
  
  Новые свойства доступны на **приложения** страницы в конструкторе проектов (Visual C# только для проектов) и формат файла проекта MSBuild.  
  
  Метод настройки создания манифеста контроля учетных Записей в Интегрированной среде разработки Visual Studio будет зависеть от типа проекта (Visual C# или Visual Basic).  
  
  * Сведения о настройке проектов Visual C# для создания манифеста см. в разделе [Application Page, Project Designer (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  * Сведения о настройке проектов Visual Basic для создания манифеста, см. в разделе [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>См. также  
 [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Разрешения пользователей и Visual Studio](https://msdn.microsoft.com/library/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)