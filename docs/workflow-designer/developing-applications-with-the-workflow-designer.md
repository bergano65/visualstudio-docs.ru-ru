---
title: Разработка приложений с помощью конструктора рабочего процесса
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
ms.openlocfilehash: ecc9e42146bfa7de259551ff1c90d27201db5725
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970129"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Разработка приложений с помощью конструктора рабочего процесса

Конструктор рабочих процессов Windows — это визуальный конструктор и отладчик для графического создания и отладки приложений Windows Workflow Foundation (WF) в .NET Framework 4, который размещен в среде разработки Visual Studio 2010. Он позволяет составлять приложения составного рабочего процесса, библиотеки действий или службы Windows Communication Foundation (WCF) с помощью шаблонов и конструкторов действий. Дополнительные сведения о рабочих процессах см. в разделе [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Ниже приведены несколько конструкторских особенностей, отделяющих эту новую версию конструктора рабочих процессов, от более старых версий конструктора рабочих процессов.

-   В конструкторе рабочих процессов построена на основе Windows Presentation Foundation (WPF). Это упрощает работу с конструктором операций и повышает производительность для сложных рабочих процессов.

-   В структуру пользовательских действий теперь включен [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], в котором используется XAML и модель программирования для упрощения создания конструкторов операций.

-   Реализовано действие создания блок-схемы, позволяющее визуализировать ход выполнения программы при помощи знакомого стиля моделирования блок-схемы.

-   В конструкторе рабочих процессов имеет новым конструктором переменных, позволяющий объявлять и собирать переменные по потокам, привязывая их к действиям.

-   В Visual Studio 2010 в конструкторе рабочих процессов предоставляет все возможности IntelliSense при создании выражений Visual Basic в рабочих процессах платформы .NET Framework 4.

-   Отладка теперь распространяется на XAML и позволяет установить точки останова в определении рабочего процесса XAML и перейти к коду XAML в пределах среды, подобно тому, как это реализовано в управляемом коде.

-   Повторное размещение конструктора рабочих процессов за пределами Visual Studio упрощено в сравнении с предыдущими версиями, и теперь требует лишь несколько строк кода.

-   Новый <xref:System.Activities.Statements.Flowchart> действия и его [блок-схема](../workflow-designer/flowchart-activity-designer.md) позволяет визуализировать ход выполнения с помощью знакомых блок-схема стиля моделирования вашей программы.

-   Улучшены действий по обмену сообщениями, позволяя писать полностью декларативные (без кода) службы Windows Communication Foundation (WCF).

-   **Добавление ссылки на службу...**  функциональность позволяет создавать действия автоматически, доступ к веб-служб.