---
title: Создание проекта Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e19ec88a4dec7a13ecc3d77e5d4fc1f04bb114bd
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747805"
---
# <a name="workflow-project-templates"></a>Шаблоны проекта workflow

С помощью шаблонов проектов Visual Studio можно создать рабочие процессы, службы рабочих процессов Windows Communication Foundation (WCF), пользовательских действий и конструкторов настраиваемых действий. В этой статье описывается создание библиотек и приложений с помощью шаблоны проектов, доступные в Visual Studio.

## <a name="create-a-workflow-project"></a>Создание проекта рабочего процесса

Visual Studio предоставляет четыре различных шаблонов проекта рабочего процесса:

- Консольное приложение рабочего процесса

- Приложение службы рабочего процесса WCF

- Библиотека действий

- Библиотека конструктора действий

Чтобы получить эти шаблоны, сначала установите **Windows Workflow Foundation** компонент Visual Studio. Подробные инструкции см. в разделе [установки Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. После установки **Windows Workflow Foundation** компонент, выберите **файл** > **New** > **проекта**.

1. Найдите и выберите шаблон проекта рабочего процесса, например, **консольное приложение рабочего процесса** шаблона.

1. Следуйте указаниям создать проект.

   > [!NOTE]
   > Если вы хотите добавить новый проект в существующее решение, откройте это решение в Visual Studio, щелкните правой кнопкой мыши решение в **обозревателе решений**и выберите **добавить** > **New Проект**.

## <a name="workflow-console-app"></a>Консольное приложение рабочего процесса

Если вы выберете **консольное приложение рабочего процесса** шаблон, Visual Studio создает определение рабочего процесса в XAML. В конструкторе рабочих процессов открывает и отображает полотно для созданного рабочего процесса. Чтобы составить рабочий процесс, перетащите действия или другие элементы рабочего процесса из **элементов** в область конструктора.

## <a name="wcf-workflow-service-app"></a>Приложение службы рабочего процесса WCF

Если вы выберете **приложение службы рабочего процесса WCF** шаблон, Visual Studio создает определение службы как XAML. Откроется конструктор рабочих процессов в режим конструктора с <xref:System.Activities.Statements.Sequence> действие, которое содержит набор <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply> действий.

## <a name="activity-library"></a>Библиотека действий

Если вы выберете **библиотеки действий** шаблон, Visual Studio создает определение в XAML. Откроется конструктор рабочих процессов и отображает полотно для настраиваемого действия. Перетащите действие из **элементов** в область конструктора, чтобы включить его в настраиваемом действии.

> [!NOTE]
> В теле настраиваемого действия разрешено только одно дочернее действие. Тем не менее, это дочернее действие может быть составным действием, например <xref:System.Activities.Statements.Sequence> действия или <xref:System.Activities.Statements.Flowchart> действия.

## <a name="activity-designer-library"></a>Библиотека конструктора действий

Если вы выберете **библиотека конструктора действий** шаблон, Visual Studio создает определение конструктора действий в XAML и кода реализации. В конструкторе рабочих процессов открывает и отображает полотно для конструктора действий. Перетащите Windows Presentation Foundation (WPF), элементы управления на **элементов** в область конструктора, чтобы использовать их в пользовательском конструкторе действий.

Пример реализации пользовательского конструктора действий, см. в разделе [как: Создание пользовательского конструктора действий](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Пользовательские конструкторы действий можно использовать для пользовательских действий, а также для действий .NET по умолчанию.

## <a name="see-also"></a>См. также

- [Использование конструктора рабочих процессов](developing-applications-with-the-workflow-designer.md)
- [Разработка рабочих процессов (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)