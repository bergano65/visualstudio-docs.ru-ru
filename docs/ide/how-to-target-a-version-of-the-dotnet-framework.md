---
title: "Практическое руководство. Определение целевой версии .NET Framework | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 50
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: eea7cb983f264fb58a4b1131f84f3ec1cb196be5
ms.contentlocale: ru-ru
ms.lasthandoff: 05/30/2017

---
# Практическое руководство. Определение целевой версии .NET Framework
<a id="how-to-target-a-version-of-the-net-framework" class="xliff"></a>
В этом документе описано, как выбрать целевую версию .NET Framework при создании проекта и как изменить целевую версию для существующего проекта Visual Basic, Visual C# или Visual F#.  
  
> [!IMPORTANT]
>  Сведения об изменении целевой версии для проектов C++ см. в разделе [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).  
  
 **Содержание раздела**  
  
-   [Выбор целевой версии при создании проекта](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
-   [Изменение целевой версии](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
##  <a name="bkmk_new"></a> Выбор целевой версии при создании проекта  
 При создании проекта целевая версия платформы .NET Framework определяет, какие шаблоны можно использовать.  
  
> [!NOTE]
>  В выпусках Visual Studio Express необходимо сначала создать проект, после чего можно будет изменить целевую версию, как описано ниже в разделе [Изменение целевой версии](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing).  
  
#### Выбор целевой версии при создании проекта
<a id="to-target-a-version-when-you-create-a-project" class="xliff"></a>  
  
1.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2.  В списке в верхней части диалогового окна **Новый проект** выберите версию .NET Framework, которая будет целевой для проекта.  
  
    > [!NOTE]
    >  Как правило, с Visual Studio устанавливается только одна версия .NET Framework. Если требуется выбрать другую целевую версию, необходимо убедиться, что она установлена. См. раздел [Обзор настройки для различных версий в Visual Studio](../ide/visual-studio-multi-targeting-overview.md).  
  
3.  Из списка установленных шаблонов выберите тип проекта, который необходимо создать, назовите проект, а затем нажмите кнопку **ОК**.  
  
     В списке шаблонов будут показаны только те проекты, которые поддерживаются выбранной версией .NET Framework.  
  
##  <a name="bkmk_existing"></a> Изменение целевой версии  
 Целевую версию .NET Framework в проекте Visual Basic, Visual C# или Visual F# можно изменить, воспользовавшись следующей процедурой.  
  
#### Изменение целевой версии
<a id="to-change-the-targeted-version" class="xliff"></a>  
  
1.  В **обозревателе решений** откройте контекстное меню проекта, для которого требуется изменить целевую платформу, и выберите пункт **Свойства**.  
  
     ![Свойства проводника Visual Studio](~/ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")  
  
    > [!IMPORTANT]
    >  Сведения об изменении целевой версии для проектов C++ см. в разделе [Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).  
  
2.  В левом столбце окна свойств перейдите на вкладку **Приложение**.  
  
     ![Вкладка "Приложение" в разделе "Свойства приложений" Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")  
  
    > [!NOTE]
    >  После создания приложения Магазина Windows невозможно изменить целевую версию Windows или .NET Framework.  
  
3.  В списке **Целевая рабочая среда** выберите требуемую версию.  
  
4.  В открывшемся диалоговом окне проверки нажмите кнопку **Да**.  
  
     Проект будет выгружен. При его перезагрузке он будет предназначен для выбранной версии .NET Framework.  
  
    > [!NOTE]
    >  Если код содержит ссылки на другую версию .NET Framework, отличную от целевой, при компиляции и запуске кода могут появиться сообщения об ошибках. Для устранения этих ошибок необходимо изменить ссылки. См. раздел [Устранение неполадок, связанных с настройкой для определенных версий платформы .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## См. также
<a id="see-also" class="xliff"></a>  
 [Обзор настройки для различных версий в Visual Studio](../ide/visual-studio-multi-targeting-overview.md)   
 [Настройка веб-проектов ASP.NET для различных версий .NET Framework](http://msdn.microsoft.com/Library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)   
 [Устранение неполадок, связанных с настройкой для определенных версий платформы .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Настройка проектов](http://msdn.microsoft.com/Library/a1489abb-6294-4f8f-b71f-2cb126393526)   
 [Практическое руководство. Изменение требуемой версии .NET Framework и набора инструментов платформы](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
