---
title: Разработка приложений с помощью конструктор рабочих процессов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848300c54800e229ee1f487fc415bad45d982a6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656830"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Разработка приложений с помощью конструктора рабочего процесса
[!INCLUDE[wfd1](../includes/wfd1-md.md)] - это визуальный конструктор и отладчик для графического создания и отладки приложений [!INCLUDE[wf](../includes/wf-md.md)] в [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)], размещенном в среде разработки [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Он позволяет создавать сложные приложения рабочего процесса, библиотеки действий и службы [!INCLUDE[indigo1](../includes/indigo1-md.md)] с помощью шаблонов и конструкторов действий. [!INCLUDE[crabout](../includes/crabout-md.md)] рабочих процессах см. [Windows Workflow Foundation &#91; .NET Framework 4&#93;](https://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Ниже представлены несколько конструкторских особенностей, отделяющих эту новую версию [!INCLUDE[wfd2](../includes/wfd2-md.md)] от более старых версий [!INCLUDE[wfd2](../includes/wfd2-md.md)]:

- [!INCLUDE[wfd2](../includes/wfd2-md.md)] построено при помощи [!INCLUDE[avalon1](../includes/avalon1-md.md)]. Это упрощает работу с конструктором операций и повышает производительность для сложных рабочих процессов.

- В структуру пользовательских действий теперь включен [!INCLUDE[avalon2](../includes/avalon2-md.md)], в котором используется XAML и модель программирования для упрощения создания конструкторов операций.

- Реализовано действие создания блок-схемы, позволяющее визуализировать поток работы программы при помощи знакомого стиля моделирования блок-схемы.

- [!INCLUDE[wfd2](../includes/wfd2-md.md)] обладает новым конструктором переменных, позволяющим объявлять и собирать переменные по потокам операций, и привязывая их к действиям.

- В [!INCLUDE[vs2010](../includes/vs2010-md.md)], [!INCLUDE[wfd2](../includes/wfd2-md.md)] позволяет реализовать все возможности IntelliSense при создании выражений Visual Basic в пределах созданных потоков операций [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

- Отладка теперь распространяется на XAML и позволяет установить точки останова в определении рабочего процесса XAML и перейти к коду XAML в пределах среды, подобно тому, как это реализовано в управляемом коде.

- Повторное размещение [!INCLUDE[wfd2](../includes/wfd2-md.md)] вне пределов [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] теперь упрощено в сравнении с предыдущими версиями, и теперь требует лишь несколько строк кода.

- Новое <xref:System.Activities.Statements.Flowchart> действие и его [блок-схема](../workflow-designer/flowchart-activity-designer.md) позволяют визуализировать ход выполнения программы с помощью привычного стиля моделирования блок-схем.

- Действия, связанные с обменом сообщениями, теперь улучшены и позволяют писать полностью декларативные (без кода) службы [!INCLUDE[indigo1](../includes/indigo1-md.md)].

- **Добавление ссылки на службу...** функция позволяет автоматически создавать действия, обращающиеся к веб-службам.

## <a name="in-this-section"></a>в этом разделе
 [Использование Конструктор рабочих процессов](../workflow-designer/using-the-workflow-designer.md) Демонстрирует создание новых действий и проектов рабочих процессов с помощью встроенных конструкторов и использование других средств, предоставляемых конструктором для обработки аргументов, переменных, выражений, импортов и навигации в виде иерархической структуры.

 [Использование конструкторов действий](../workflow-designer/using-the-activity-designers.md) Описывает категории действий и шаблонов, а также их конструкторы, предоставляемые системой.

 [Отладка рабочих процессов с помощью Конструктор рабочих процессов](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) Опишите выполнение традиционных процедур отладки, а также отладку XAML и выражений.

 [Справка по пользовательскому интерфейсу конструктор рабочих процессов](../workflow-designer/workflow-designer-ui-help.md) Содержит разделы контекстной справки для диалоговых окон, предоставляемых [!INCLUDE[wfd1](../includes/wfd1-md.md)] , а также руководство по функциям оболочки конструктора, сочетаниям клавиш и сообщениям об ошибках.

 [Разработка приложений рабочих процессов, предназначенных для платформы .net 3,0 или .net 3,5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md) Содержит рекомендации по использованию конструктора предыдущих версий, предназначенного для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Повторное [размещение конструктора &#91;примеры WF&#93;](https://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d) В этом примере показано, как создать макет WPF для размещения конструктора.

 [Конструкторы настраиваемых действий](https://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075) В этом разделе содержатся примеры действий, в которых используются пользовательские конструкторы для вывода в конструкторе рабочих процессов.