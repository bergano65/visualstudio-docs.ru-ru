---
title: Разработка приложений с помощью конструктора рабочих процессов | Документы Microsoft
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c48e7b43b23e7bfe8887f437cc17e6db077c0e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="developing-applications-with-the-workflow-designer"></a>Разработка приложений с помощью конструктора рабочего процесса

Конструктор рабочих процессов Windows — это визуальный конструктор и отладчик для графического создания и отладки [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] приложений в [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] , размещенном в [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] среды разработки. Он позволяет создавать сложные приложения рабочего процесса, библиотеки действий и службы [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] с помощью шаблонов и конструкторов действий. Дополнительные сведения о рабочих процессах см. в разделе [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

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