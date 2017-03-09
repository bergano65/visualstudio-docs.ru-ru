---
title: "Обзор настройки для различных версий в Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "настройка для различных версий [Visual Studio]"
  - "настройка для различных версий [Visual Studio]"
  - "настройка версии платформы .NET Framework [Visual Studio]"
  - "версии [Visual Studio], настройка версии платформы .NET Framework"
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 36
caps.handback.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Обзор настройки для различных версий в Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этой версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], можно указать версию  [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], необходимую для приложения.  Поэтому, если требуется использовать эту версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], чтобы продолжить разработку проекта, который был начат в более ранней версии, менять целевую платформу не нужно.  Также можно создать решение, содержащее проекты различных версий этого целевого объекта платформы.  Настройка для платформы помогает гарантировать, что приложение используют только функциональные возможности, доступные в указанной версии платформы.  
  
> [!TIP]
>  Можно также ориентировать приложения для других платформ.  Дополнительные сведения см. в разделе [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md).  
  
## Возможности настройки для платформы  
 Настройка для платформы включает следующие функции:  
  
-   Если открывается проект, ориентированный на более раннюю версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] может автоматически обновить его или оставить его как есть.  
  
-   При создании проекта можно указать версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], на которую будет ориентирован проект.  
  
-   Можно изменить версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], на которую ориентирован существующий проект.  
  
-   В одном решении можно использовать различные версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] для каждого из нескольких проектов.  
  
-   При изменении версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], на которую ориентирован проект, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] вносит все необходимые изменения в ссылки и файлы конфигурации.  
  
 При работе над проектом, ориентированным на более раннюю версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio динамически вносит изменения в среду разработки, например следующие:  
  
-   Фильтрует элементы в диалоговых окнах **Создать проект**, **Добавить новый элемент**, **Добавить новую ссылку** и **Добавить ссылку на службу**, чтобы избежать вариантов выбора, недоступные в целевой версии.  
  
-   Фильтрует пользовательские элементы управления в **Панели элементов**, чтобы удалить элементы, не доступные в целевой версии и показывающие только самую последнюю версию элементов управления, если доступно несколько элементов управления.  
  
-   Фильтрует IntelliSense, чтобы пропустить функции языка, недоступные в целевой версии.  
  
-   Фильтрует свойства в окне **Свойства**, чтобы исключить свойства, недоступные в целевой версии.  
  
-   Фильтрует пункты меню, чтобы исключить пункты, недоступные в целевой версии.  
  
-   Для сборок он использует версии компилятора и параметры компилятора, соответствующие целевой версии.  
  
> [!NOTE]
>  Настройка для платформы не гарантирует, что приложение будет работать правильно.  Чтобы убедиться в работоспособности приложения в целевой версии, необходимо его протестировать.  Невозможно ориентироваться на более ранние версии платформы, чем .NET Framework 2.0.  
  
## Выбор версии целевой платформы  
 При создании проекта выберите версию целевого объекта [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] в диалоговом окне **Создать проект**.  Список доступных шаблонов проектов фильтруется на основании выбора.  В существующем проекте можно изменить целевую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] в диалоговом окне свойств проекта.  Для получения дополнительной информации см. [Практическое руководство. Определение целевой версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
> [!NOTE]
>  В выпусках Visual Studio Express невозможно задать целевую платформу в диалоговом окне **Создать проект**.  
  
## Обработка системных и пользовательских ссылок на сборки  
 Для нацеливания на определенную версию платформы .NET Framework необходимо сначала установить соответствующие ссылки на сборки.  Ссылки на сборки для версий .NET Framework 2.0, 3.0 и 3.5 включены в состав платформы .NET Framework 3.5 SP1, которые можно загрузить с веб\-сайта [Центра загрузки Майкрософт, Microsoft Visual Studio](http://go.microsoft.com/fwlink/?LinkId=227602).  Ссылки на сборки для профилей клиента .NET Framework 3.5, .NET Framework 4, .NET Framework 4 \(клиентский профиль\) и Silverlight также доступны с веб\-сайта [Загрузки Visual Studio](http://go.microsoft.com/fwlink/?LinkId=179687).  
  
> [!NOTE]
>  Клиентский профиль .NET Framework — это подмножество .NET Framework, предоставляющее ограниченный набор библиотек и функций.  Дополнительные сведения о клиентских профилях см. в разделе [Профиль клиента .NET Framework](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
 Диалоговое окно **Добавить ссылку** делает недоступными системные сборки, которые не относятся к целевой версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], чтобы их невозможно было случайно добавить в проект. \(Системные сборки — это файлы DLL, включенные в версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].\) Ссылки, которые относятся к версии платформы более поздней, чем целевая версия, не будут разрешены, и элементы управления, зависящие от таких ссылок, невозможно будет добавить.  Если необходимо включить такую ссылку, сбросьте целевой объект [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] проекта на такой, который включает ссылку.  Дополнительные сведения см. в разделе [Introduction to the Project Designer](http://msdn.microsoft.com/ru-ru/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
 Дополнительные сведения о ссылках на сборки см. в разделе [Разрешение сборок во время разработки](../msbuild/resolving-assemblies-at-design-time.md).  
  
## Включение LINQ  
 При нацеливании проекта на платформу .NET Framework 3.5 или более позднюю версию ссылка на System.Core и импорт на уровне проекта System.Linq \(только в Visual Basic\) добавляются автоматически.  Чтобы использовать возможности LINQ, необходимо также включить Option Infer \(только в Visual Basic\).  При изменении требуемой версии .NET Framework более раннюю версию ссылка и импорт автоматически удаляются.  Для получения дополнительной информации см. [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## См. также  
 [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md)   
 [.NET Framework Multi\-Targeting for ASP.NET Web Projects](../Topic/.NET%20Framework%20Multi-Targeting%20for%20ASP.NET%20Web%20Projects.md)   
 [Совместимость платформ и системные требования](http://www.microsoft.com/visualstudio/eng/products/compatibility)