---
title: "Разработка приложений с помощью конструктора рабочего процесса | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "DefaultWorkflowDesigner"
  - "DefaultWorkflowDesigner.UI"
helpviewer_keywords: 
  - "конструктор рабочих процессов Visual Studio 2010 [WFD]"
  - "конструктор рабочих процессов Visual Studio 2010 [WFD], общие сведения"
  - "конструктор рабочих процессов [WFD]"
  - "конструктор рабочих процессов [WFD], общие сведения"
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
caps.handback.revision: 17
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Разработка приложений с помощью конструктора рабочего процесса
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] — это визуальный конструктор и отладчик для графического создания и отладки приложений [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] в [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)], размещенном в среде разработки [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].Он позволяет создавать сложные приложения рабочего процесса, библиотеку действий или службу [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] за счет использования шаблонов и конструкторов действий.[!INCLUDE[crabout](../test/includes/crabout_md.md)] рабочих процессах см.в разделе [Windows Workflow Foundation](../Topic/Windows%20Workflow%20Foundation.md).  
  
 Ниже представлены несколько конструкторских особенностей, отделяющих эту новую версию [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] от более старых версий [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]:  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] построено при помощи [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)].Это упрощает работу с конструктором операций и повышает производительность для сложных рабочих процессов.  
  
-   В структуру пользовательских действий теперь включен [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], в котором используется XAML и модель программирования для упрощения создания конструкторов операций.  
  
-   Реализовано действие создания блок\-схемы, позволяющее визуализировать ход выполнения программы при помощи знакомого стиля моделирования блок\-схемы.  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] обладает новым конструктором переменных, позволяющим объявлять и собирать переменные по потокам операций, и привязывая их к действиям.  
  
-   В [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] позволяет реализовать все возможности IntelliSense при создании выражений Visual Basic в пределах созданных потоков операций [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].  
  
-   Отладка теперь распространяется на XAML и позволяет установить точки останова в определении рабочего процесса XAML и перейти к коду XAML в пределах среды, подобно тому, как это реализовано в управляемом коде.  
  
-   Повторное размещение [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] вне пределов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] теперь упрощено в сравнении с предыдущими версиями, и теперь требует лишь несколько строк кода.  
  
-   Новые действия <xref:System.Activities.Statements.Flowchart> и [Блок\-схема](../workflow-designer/flowchart-activity-designer.md) позволяют виртуализировать выполнение программы при помощи знакомого стиля моделирования блок\-схемы.  
  
-   Действия, связанные с обменом сообщениями, теперь улучшены и позволяют писать полностью декларативные \(без кода\) службы [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)].  
  
-   Функция **Добавить ссылку на службу…** позволяет автоматически создавать действия, которые осуществляют доступ к веб\-службам.  
  
## В этом подразделе  
 [Использование конструктора рабочих процессов](../workflow-designer/using-the-workflow-designer.md)  
 Показывает, как создать новые действия и проекты рабочего процесса с использованием встроенных конструкторов, а также как использовать другие средства, предоставляемые конструктором, для обработки аргументов, переменных, выражений, операций импорта и строки навигации.  
  
 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md)  
 Описывает категории действий, шаблоны и соответствующие конструкторы, предоставляемые системой.  
  
 [Отладка рабочих процессов с помощью конструктора рабочих процессов](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Описывает, как выполнить традиционные процедуры отладки, а также отладку XAML и выражений.  
  
 [Справка по пользовательскому интерфейсу конструктора рабочих процессов](../workflow-designer/workflow-designer-ui-help.md)  
 Содержит разделы контекстной справки для диалоговых окон, входящих в [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], а также руководство по функциям оболочки конструктора, сочетаниям клавиш и сообщениям об ошибке.  
  
 [Разработка приложений рабочих процессов, предназначенных для платформы .NET 3.0 или .NET 3.5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Содержит руководство по использованию конструктора прежних версий, предназначенного для работы с [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [Повторное размещение конструктора &#91;образцы WF&#93;](../Topic/Designer%20ReHosting.md)  
 В этом образце показано, как создать макет WPF, содержащий конструктор.  
  
 [Пользовательские конструкторы действий](../Topic/Custom%20Activity%20Designers.md)  
 В данном разделе содержатся образцы действий, использующих пользовательские конструкторы для отображения в конструкторе рабочих процессов.