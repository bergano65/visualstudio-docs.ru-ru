---
title: Практическое руководство. Определение целевой версии .NET Framework | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9cd6c42788ee0b3cafab695ffed61323a6d81205
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570576"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Практическое руководство. Определение целевой версии .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Определение целевой версии платформы .NET Framework](https://docs.microsoft.com/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).  
  
В этом документе описано, как выбрать целевую версию .NET Framework при создании проекта и как изменить целевую версию для существующего проекта Visual Basic, Visual C# или Visual F#.  
  
> [!IMPORTANT]
>  Сведения об изменении целевой версии для проектов C++ см. в разделе [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
 **Содержание раздела**  
  
-   [Выбор целевой версии при создании проекта](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
-   [Изменение целевой версии](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
##  <a name="bkmk_new"></a> Выбор целевой версии при создании проекта  
 При создании проекта целевая версия платформы .NET Framework определяет, какие шаблоны можно использовать.  
  
> [!NOTE]
>  В выпусках Visual Studio Express необходимо сначала создать проект, после чего можно будет изменить целевую версию, как описано ниже в разделе [Изменение целевой версии](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing).  
  
#### <a name="to-target-a-version-when-you-create-a-project"></a>Выбор целевой версии при создании проекта  
  
1.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2.  В списке в верхней части диалогового окна **Новый проект** выберите версию .NET Framework, которая будет целевой для проекта.  
  
    > [!NOTE]
    >  Как правило, с Visual Studio устанавливается только одна версия .NET Framework. Если требуется выбрать другую целевую версию, необходимо убедиться, что она установлена. См. раздел [Обзор настройки для различных версий в Visual Studio](../ide/visual-studio-multi-targeting-overview.md).  
  
3.  Из списка установленных шаблонов выберите тип проекта, который необходимо создать, назовите проект, а затем нажмите кнопку **ОК**.  
  
     В списке шаблонов будут показаны только те проекты, которые поддерживаются выбранной версией .NET Framework.  
  
##  <a name="bkmk_existing"></a> Изменение целевой версии  
 Целевую версию .NET Framework в проекте Visual Basic, Visual C# или Visual F# можно изменить, воспользовавшись следующей процедурой.  
  
#### <a name="to-change-the-targeted-version"></a>Изменение целевой версии  
  
1.  В **обозревателе решений** откройте контекстное меню проекта, для которого требуется изменить целевую платформу, и выберите пункт **Свойства**.  
  
     ![Свойства проводника Visual Studio](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")  
  
    > [!IMPORTANT]
    >  Сведения об изменении целевой версии для проектов C++ см. в разделе [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
2.  В левом столбце окна свойств перейдите на вкладку **Приложение**.  
  
     ![Вкладка "Приложение" в разделе "Свойства приложений" Visual Studio](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")  
  
    > [!NOTE]
    >  После создания приложения Магазина Windows невозможно изменить целевую версию Windows или .NET Framework.  
  
3.  В списке **Целевая рабочая среда** выберите требуемую версию.  
  
4.  В открывшемся диалоговом окне проверки нажмите кнопку **Да**.  
  
     Проект будет выгружен. При его перезагрузке он будет предназначен для выбранной версии .NET Framework.  
  
    > [!NOTE]
    >  Если код содержит ссылки на другую версию .NET Framework, отличную от целевой, при компиляции и запуске кода могут появиться сообщения об ошибках. Для устранения этих ошибок необходимо изменить ссылки. См. раздел [Устранение неполадок, связанных с настройкой для определенных версий платформы .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## <a name="see-also"></a>См. также  
 [Обзор настройки для различных версий в Visual Studio](../ide/visual-studio-multi-targeting-overview.md)   
 [Настройка веб-проектов ASP.NET для различных версий .NET Framework](http://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)   
 [Устранение неполадок, связанных с настройкой для определенных версий платформы .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Настройка проектов](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)   
 [Практическое руководство. Изменение требуемой версии .NET Framework и набора инструментов платформы](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)



