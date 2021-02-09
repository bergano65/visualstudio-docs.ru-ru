---
title: Развертывание ClickOnce в Windows Vista | Документация Майкрософт
description: Узнайте, как Visual Studio создает внешний манифест UAC для ClickOnce и Registration-Free COM-приложений, для которых требуется внешний манифест.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ccac1cd234a0f83810ff2596e1763209d95a8325
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918444"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Развертывание ClickOnce в Windows Vista

Создание приложений в Visual Studio для контроля учетных записей (UAC) в Windows Vista обычно создает внедренный манифест, закодированный как двоичные XML-данные в исполняемом файле приложения.  Приложениям ClickOnce и Registration-Free COM требуется внешний манифест, поэтому Visual Studio создает файл для этих проектов, содержащих данные контроля учетных записей, а не внедренный манифест. Для развертывания ClickOnce и Registration-Free развертываний COM в Visual Studio используются сведения из файла с именем *app. manifest* для создания сведений о внешнем манифесте UAC. Во всех остальных случаях Visual Studio внедряет данные контроля учетных записей в исполняемый файл приложения.

Visual Studio предоставляет следующие возможности для создания манифеста:

- Используйте внедренный манифест. Внедрение данных контроля учетных записей в исполняемый файл приложения и запуск от имени обычного пользователя.

   Это значение по умолчанию (если не используется технология ClickOnce). Этот параметр поддерживает обычный способ работы Visual Studio в Windows Vista с созданием внутреннего и внешнего манифеста с помощью `AsInvoker` .

- Используйте внешний манифест. Создание внешнего манифеста с помощью *app. manifest*.

   При этом создается только внешний манифест с использованием сведений в файле *app. manifest*. При публикации приложения с помощью ClickOnce или Registration-Free COM Visual Studio добавляет в проект *app. manifest* , а затем добавляет этот параметр.

- Не использовать манифест. Создайте приложение без манифеста.

   Этот подход также известен как *виртуализация*. Используйте этот параметр для совместимости с существующими приложениями из более ранних версий Visual Studio.

  Новые свойства доступны на странице **приложение** конструктора проектов (только для проектов Visual C#) и в формате файла проекта MSBuild.

  Метод настройки создания манифеста UAC в интегрированной среде разработки Visual Studio зависит от типа проекта (Visual C# или Visual Basic).

  * Сведения о настройке проектов Visual C# для создания манифеста см. в разделе [Страница "приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * Сведения о настройке проектов Visual Basic для создания манифеста см. в разделе [Страница "приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>См. также раздел
- [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Разрешения пользователей и Visual Studio](/previous-versions/ms165100(v=vs.100))
- [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)