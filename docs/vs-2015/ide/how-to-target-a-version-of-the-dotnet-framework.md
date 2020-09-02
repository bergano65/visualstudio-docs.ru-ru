---
title: Практическое руководство. Определение целевой версии .NET Framework | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7aae21e2c959939262b88db3b90367c4860d8a74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670621"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Практическое руководство. Определение целевой версии .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом документе описано, как выбрать целевую версию .NET Framework при создании проекта и как изменить целевую версию для существующего проекта Visual Basic, Visual C# или Visual F#.

> [!IMPORTANT]
> Сведения о том, как изменить целевую версию для проектов C++, см. в разделе [руководство. изменение целевой платформы и набора инструментов платформы](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).

 **Содержание раздела**

- [Нацеливание на версию при создании проекта](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)

- [Изменение целевой версии](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)

## <a name="targeting-a-version-when-you-create-a-project"></a><a name="bkmk_new"></a> Выбор целевой версии при создании проекта
 При создании проекта целевая версия платформы .NET Framework определяет, какие шаблоны можно использовать.

> [!NOTE]
> В выпусках Visual Studio Express необходимо сначала создать проект, после чего можно будет изменить целевую версию, как описано ниже в разделе [Изменение целевой версии](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing).

#### <a name="to-target-a-version-when-you-create-a-project"></a>Выбор целевой версии при создании проекта

1. В строке меню выберите **Файл**, **Создать**, **Проект**.

2. В списке в верхней части диалогового окна **Новый проект** выберите версию .NET Framework, которая будет целевой для проекта.

    > [!NOTE]
    > Как правило, с Visual Studio устанавливается только одна версия .NET Framework. Если требуется выбрать другую целевую версию, необходимо убедиться, что она установлена. См. раздел [Обзор настройки для различных версий в Visual Studio](../ide/visual-studio-multi-targeting-overview.md).

3. Из списка установленных шаблонов выберите тип проекта, который необходимо создать, назовите проект, а затем нажмите кнопку **ОК**.

     В списке шаблонов будут показаны только те проекты, которые поддерживаются выбранной версией .NET Framework.

## <a name="changing-the-target-version"></a><a name="bkmk_existing"></a> Изменение целевой версии
 Целевую версию .NET Framework в проекте Visual Basic, Visual C# или Visual F# можно изменить, воспользовавшись следующей процедурой.

#### <a name="to-change-the-targeted-version"></a>Изменение целевой версии

1. В **обозревателе решений** откройте контекстное меню проекта, для которого требуется изменить целевую платформу, и выберите пункт **Свойства**.

     ![Свойства проводника Visual Studio](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")

    > [!IMPORTANT]
    > Сведения о том, как изменить целевую версию для проектов C++, см. в разделе [руководство. изменение целевой платформы и набора инструментов платформы](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).

2. В левом столбце окна Свойства перейдите на вкладку **приложение** .

     ![Вкладка "Приложение" в разделе "Свойства приложений" Visual Studio](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > После создания приложения Магазина Windows невозможно изменить целевую версию Windows или .NET Framework.

3. В списке **Целевая рабочая среда** выберите требуемую версию.

4. В открывшемся диалоговом окне проверки нажмите кнопку **Да**.

     Проект будет выгружен. При его перезагрузке он будет предназначен для выбранной версии .NET Framework.

    > [!NOTE]
    > Если код содержит ссылки на другую версию .NET Framework, отличную от целевой, при компиляции и запуске кода могут появиться сообщения об ошибках. Для устранения этих ошибок необходимо изменить ссылки. См. раздел [Устранение неполадок, связанных с настройкой для определенных версий платформы .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>См. также:
 Обзор многоплатформенного [нацеливания в Visual Studio общие сведения .NET Framework об](../ide/visual-studio-multi-targeting-overview.md) [устранении неполадок](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md) [для веб-проектов ASP.NET](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76) . .NET Framework [Страница "приложения", конструктор проектов (C#)](../ide/reference/application-page-project-designer-csharp.md) , страница "приложение", [Конструктор проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) [Настройка проектов](https://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526) [руководство. изменение целевой платформы и набора инструментов платформы](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)
