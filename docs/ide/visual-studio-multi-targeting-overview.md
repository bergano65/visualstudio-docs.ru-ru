---
title: "Обзор настройки для различных версий в Visual Studio| Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ad2917a1cf0a620f2e228828a152d91ec8948734
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-multi-targeting-overview"></a>Обзор настройки для различных версий в Visual Studio
В этой версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] можно указать версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], необходимую для вашего приложения. Таким образом, если вы хотите использовать эту версию [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для продолжения разработки проекта, работу над которым начали в более ранней версии, вам не нужно изменять целевую версию платформы .NET Framework. Можно также создать решение, содержащее проекты, ориентированные на разные версии платформы. Нацеливание платформы также помогает гарантировать, что приложение использует только те функциональные возможности, которые доступны в указанной версии платформы.  
  
> [!TIP]
>  Вы также можете нацеливать приложения на различные платформы. Дополнительные сведения см. в разделе [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md).  
  
## <a name="framework-targeting-features"></a>Функции нацеливания на платформу  
 Среди прочего, доступны следующие возможности нацеливания на платформу:  
  
-   При открытии проекта, который ориентирован на более раннюю версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] может автоматически обновить его или оставить имеющуюся настройку.  
  
-   При создании проекта можно указать версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], на которую требуется ориентироваться.  
  
-   Можно изменить версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], на которую ориентирован существующий проект.  
  
-   В каждом из нескольких проектов в одном решении можно ориентироваться на разные версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
-   При изменении версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], на которую сориентирован проект, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] вносит все необходимые изменения в ссылки и файлы конфигурации.  
  
 При работе над проектом, нацеленным на более раннюю версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio динамически изменяет среду разработки, как показано ниже:  
  
-   Фильтрует элементы в диалоговых окнах **Новый проект** **Добавить новый элемент** **Добавить новую ссылку** и **Добавление ссылки на службу**, чтобы пропустить варианты, которые недоступны в целевой версии.  
  
-   Фильтрует пользовательские элементы управления на **панели элементов**, чтобы удалить те из них, которые недоступны в целевой версии, и отобразить только наиболее актуальные элементы, если доступно несколько элементов управления.  
  
-   Фильтрует IntelliSense, чтобы пропустить языковые функции, которые недоступны в целевой версии.  
  
-   Фильтрует свойства в окне **Свойства**, чтобы пропустить те, которые недоступны в целевой версии.  
  
-   Фильтрует пункты меню, чтобы пропустить те, которые не доступны в целевой версии.  
  
-   Для сборок система использует версию и параметры компилятора, которые подходят для целевой версии.  
  
> [!NOTE]
>  Нацеливание на платформу не гарантирует правильную работу приложения. Нужно протестировать приложение, чтобы убедиться в том, что оно работает с целевой версией. Нельзя выбрать в качестве целевых версий платформы, предшествующие .NET Framework 2.0.  
  
## <a name="selecting-a-target-framework-version"></a>Выбор целевой версии платформы  
 При создании проекта выберите целевую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] в диалоговом окне **Новый проект**. Список доступных шаблонов проектов фильтруется в зависимости от выбранного значения. Для существующего проекта можно изменить целевую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] в диалоговом окне свойств проекта. Дополнительные сведения см. в разделе [Практическое руководство. Настройка конкретной версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
> [!NOTE]
>  В выпусках Visual Studio Express нельзя задать целевую платформу в диалоговом окне **Новый проект**.  
  
## <a name="resolving-system-and-user-assembly-references"></a>Разрешение системных ссылок и пользовательских ссылок на сборки  
 Чтобы нацелиться на определенную версию .NET Framework, нужно сначала установить подходящие ссылки на сборки. Ссылки на сборки для .NET Framework версий 2.0, 3.0 и 3.5 включены в пакет обновления 1 (SP1) для .NET Framework 3.5, который можно скачать на веб-сайте [Центра загрузки Майкрософт, Microsoft Visual Studio](http://go.microsoft.com/fwlink/?LinkId=227602). Ссылки на сборки для клиентского профиля .NET Framework 3.5, .NET Framework 4, клиентского профиля .NET Framework 4 и Silverlight также доступны на веб-сайте [скачиваемых материалов для Visual Studio](http://go.microsoft.com/fwlink/?LinkId=179687).  
  
> [!NOTE]
>  Клиентский профиль .NET Framework — это подмножество компонентов .NET Framework, предоставляющее ограниченный набор библиотек и функций. Дополнительные сведения о клиентских профилях см. в разделе [Клиентский профиль .NET Framework](/dotnet/framework/deployment/client-profile).  
  
 Диалоговое окно **Добавить ссылку** позволяет отключить системные сборки, не относящиеся к целевой версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], чтобы их нельзя было добавить в проект случайно. (Системные сборки — это DLL-файлы, включенные в версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].) Ссылки, которые относятся к версии платформы, которая старше целевой версии, не будут разрешены, а зависящие от них элементы управления невозможно будет добавить. Если вы хотите активировать такую ссылку, измените целевую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] для проекта на ту, которая содержит эту ссылку.  Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
 Дополнительные сведения о ссылках на сборки см. в разделе [Разрешение сборок во время разработки](../msbuild/resolving-assemblies-at-design-time.md).  
  
## <a name="enabling-linq"></a>Включение LINQ  
 При нацеливании на .NET Framework 3.5 или более поздней версии ссылка на System.Core и импорт уровня проекта для System.Linq (в Visual Basic) добавляются автоматически. Если вы хотите использовать функции LINQ, нужно также включить параметр "Option Infer on" (только в Visual Basic). Ссылка и импорт удаляются автоматически при изменении целевой версии на более раннюю версию .NET Framework. Дополнительные сведения см. в разделе [Работа с LINQ](/dotnet/csharp/tutorials/working-with-linq).  
  
## <a name="see-also"></a>См. также  
 [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md)   
 [Совместимость платформ и требования к системе](http://www.microsoft.com/visualstudio/eng/products/compatibility)