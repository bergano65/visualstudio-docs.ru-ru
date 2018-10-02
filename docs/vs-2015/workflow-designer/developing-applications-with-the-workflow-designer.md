---
title: Разработка приложений с помощью конструктора рабочих процессов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6a010a0df75e683ad26ac0ca297a0ab817bd22cd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557930"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Разработка приложений с помощью конструктора рабочего процесса
[!INCLUDE[wfd1](../includes/wfd1-md.md)] - это визуальный конструктор и отладчик для графического создания и отладки приложений [!INCLUDE[wf](../includes/wf-md.md)] в [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)], размещенном в среде разработки [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Он позволяет создавать сложные приложения рабочего процесса, библиотеки действий и службы [!INCLUDE[indigo1](../includes/indigo1-md.md)] с помощью шаблонов и конструкторов действий. [!INCLUDE[crabout](../includes/crabout-md.md)] рабочие процессы, см. в разделе [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).  
  
 Ниже представлены несколько конструкторских особенностей, отделяющих эту новую версию [!INCLUDE[wfd2](../includes/wfd2-md.md)] от более старых версий [!INCLUDE[wfd2](../includes/wfd2-md.md)]:  
  
-   [!INCLUDE[wfd2](../includes/wfd2-md.md)] построено при помощи [!INCLUDE[avalon1](../includes/avalon1-md.md)]. Это упрощает работу с конструктором операций и повышает производительность для сложных рабочих процессов.  
  
-   В структуру пользовательских действий теперь включен [!INCLUDE[avalon2](../includes/avalon2-md.md)], в котором используется XAML и модель программирования для упрощения создания конструкторов операций.  
  
-   Реализовано действие создания блок-схемы, позволяющее визуализировать ход выполнения программы при помощи знакомого стиля моделирования блок-схемы.  
  
-   [!INCLUDE[wfd2](../includes/wfd2-md.md)] обладает новым конструктором переменных, позволяющим объявлять и собирать переменные по потокам операций, и привязывая их к действиям.  
  
-   В [!INCLUDE[vs2010](../includes/vs2010-md.md)], [!INCLUDE[wfd2](../includes/wfd2-md.md)] позволяет реализовать все возможности IntelliSense при создании выражений Visual Basic в пределах созданных потоков операций [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].  
  
-   Отладка теперь распространяется на XAML и позволяет установить точки останова в определении рабочего процесса XAML и перейти к коду XAML в пределах среды, подобно тому, как это реализовано в управляемом коде.  
  
-   Повторное размещение [!INCLUDE[wfd2](../includes/wfd2-md.md)] вне пределов [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] теперь упрощено в сравнении с предыдущими версиями, и теперь требует лишь несколько строк кода.  
  
-   Новый <xref:System.Activities.Statements.Flowchart> действия и его [блок-схема](../workflow-designer/flowchart-activity-designer.md) позволяют виртуализировать выполнение программы с помощью знакомого блок-схемы, стиля моделирования.  
  
-   Действия, связанные с обменом сообщениями, теперь улучшены и позволяют писать полностью декларативные (без кода) службы [!INCLUDE[indigo1](../includes/indigo1-md.md)].  
  
-   **Добавление ссылки на службу...** функциональность позволяет создавать действия автоматически, доступ к веб-служб.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Использование конструктора рабочих процессов](../workflow-designer/using-the-workflow-designer.md)  
 Показывает, как создать новые действия и проекты рабочего процесса с использованием встроенных конструкторов, а также как использовать другие средства, предоставляемые конструктором, для обработки аргументов, переменных, выражений, операций импорта и строки навигации.  
  
 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md)  
 Описывает категории действий, шаблоны и соответствующие конструкторы, предоставляемые системой.  
  
 [Отладка рабочих процессов с помощью конструктора рабочих процессов](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Описывает, как выполнить традиционные процедуры отладки, а также отладку XAML и выражений.  
  
 [Справка по пользовательскому интерфейсу конструктора рабочих процессов](../workflow-designer/workflow-designer-ui-help.md)  
 Содержит разделы контекстной справки для диалоговых окон, входящих в [!INCLUDE[wfd1](../includes/wfd1-md.md)], а также руководство по функциям оболочки конструктора, сочетаниям клавиш и сообщениям об ошибке.  
  
 [Разработка приложений рабочих процессов, предназначенных для платформы .NET 3.0 или .NET 3.5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Содержит руководство по использованию конструктора прежних версий, предназначенного для работы с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 [Повторному размещению конструктора &#91;образцы WF&#93;](http://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 В этом образце показано, как создать макет WPF, содержащий конструктор.  
  
 [Пользовательские конструкторы действий](http://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075)  
 В данном разделе содержатся образцы действий, использующих пользовательские конструкторы для отображения в конструкторе рабочих процессов.