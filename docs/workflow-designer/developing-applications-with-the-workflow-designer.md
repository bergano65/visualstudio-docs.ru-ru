---
title: "Разработка приложений с помощью конструктора рабочих процессов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: "17"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: cbb7b09e5c36980ceeedd99f69241996bd25bfa3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="developing-applications-with-the-workflow-designer"></a>Разработка приложений с помощью конструктора рабочего процесса
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] - это визуальный конструктор и отладчик для графического создания и отладки приложений [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] в [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)], размещенном в среде разработки [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Он позволяет создавать сложные приложения рабочего процесса, библиотеки действий и службы [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] с помощью шаблонов и конструкторов действий. [!INCLUDE[crabout](../test/includes/crabout_md.md)]рабочие процессы, в разделе [Windows Workflow Foundation &#91;. .NET Framework 4 &#93; ](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).  
  
 Ниже представлены несколько конструкторских особенностей, отделяющих эту новую версию [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] от более старых версий [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]:  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] построено при помощи [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)]. Это упрощает работу с конструктором операций и повышает производительность для сложных рабочих процессов.  
  
-   В структуру пользовательских действий теперь включен [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], в котором используется XAML и модель программирования для упрощения создания конструкторов операций.  
  
-   Реализовано действие создания блок-схемы, позволяющее визуализировать ход выполнения программы при помощи знакомого стиля моделирования блок-схемы.  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] обладает новым конструктором переменных, позволяющим объявлять и собирать переменные по потокам операций, и привязывая их к действиям.  
  
-   В [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] позволяет реализовать все возможности IntelliSense при создании выражений Visual Basic в пределах созданных потоков операций [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].  
  
-   Отладка теперь распространяется на XAML и позволяет установить точки останова в определении рабочего процесса XAML и перейти к коду XAML в пределах среды, подобно тому, как это реализовано в управляемом коде.  
  
-   Повторное размещение [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] вне пределов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] теперь упрощено в сравнении с предыдущими версиями, и теперь требует лишь несколько строк кода.  
  
-   Новый <xref:System.Activities.Statements.Flowchart> действия и его [блок-схема](../workflow-designer/flowchart-activity-designer.md) позволяет визуализировать ход выполнения с помощью знакомых блок-схема стиля моделирования вашей программы.  
  
-   Действия, связанные с обменом сообщениями, теперь улучшены и позволяют писать полностью декларативные (без кода) службы [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)].  
  
-   **Добавление ссылки на службу...**  функциональность позволяет создавать действия автоматически, доступ к веб-служб.  
  
## <a name="in-this-section"></a>Содержание  
 [Использование конструктора рабочих процессов](../workflow-designer/using-the-workflow-designer.md)  
 Показывает, как создать новые действия и проекты рабочего процесса с использованием встроенных конструкторов, а также как использовать другие средства, предоставляемые конструктором, для обработки аргументов, переменных, выражений, операций импорта и строки навигации.  
  
 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md)  
 Описывает категории действий, шаблоны и соответствующие конструкторы, предоставляемые системой.  
  
 [Отладка рабочих процессов с помощью конструктора рабочих процессов](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Описывает, как выполнить традиционные процедуры отладки, а также отладку XAML и выражений.  
  
 [Справка по пользовательскому интерфейсу конструктора рабочих процессов](../workflow-designer/workflow-designer-ui-help.md)  
 Содержит разделы контекстной справки для диалоговых окон, входящих в [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], а также руководство по функциям оболочки конструктора, сочетаниям клавиш и сообщениям об ошибке.  
  
 [Разработка приложений рабочих процессов, предназначенных для платформы .NET 3.0 или .NET 3.5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Содержит руководство по использованию конструктора прежних версий, предназначенного для работы с [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [Повторное размещение конструктора &#91; Образцы WF &#93;](http://msdn.microsoft.com/Library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 В этом образце показано, как создать макет WPF, содержащий конструктор.  
  
 [Пользовательские конструкторы действий](/dotnet/framework/windows-workflow-foundation/samples/custom-activity-designers)  
 В данном разделе содержатся образцы действий, использующих пользовательские конструкторы для отображения в конструкторе рабочих процессов.