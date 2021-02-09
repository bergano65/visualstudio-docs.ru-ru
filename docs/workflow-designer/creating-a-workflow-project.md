---
title: Создание проекта Workflow Foundation
description: Узнайте, как создавать библиотеки и приложения с помощью шаблонов проектов, доступных в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cf8c0fe0b716cecee19c00bb0b300d4ffdc99355
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894365"
---
# <a name="workflow-project-templates"></a>Шаблоны проектов рабочих процессов

Вы можете создавать рабочие процессы, службы рабочих процессов Windows Communication Foundation (WCF), пользовательские действия и конструкторы настраиваемых действий с помощью шаблонов проектов Visual Studio. В этой статье описывается создание библиотек и приложений с помощью шаблонов проектов, доступных в Visual Studio.

## <a name="create-a-workflow-project"></a>Создание проекта рабочего процесса

Visual Studio предоставляет четыре разных шаблона проекта рабочего процесса:

- Консольное приложение рабочего процесса

- Приложение службы рабочего процесса WCF

- Библиотека действий

- Библиотека конструктора действий

Чтобы получить доступ к этим шаблонам, сначала установите компонент **Windows Workflow Foundation** Visual Studio. Подробные инструкции см. в разделе [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. После установки компонента **Windows Workflow Foundation** выберите **файл**  >  **создать**  >  **проект**.

1. Найдите и выберите шаблон проекта рабочего процесса, например шаблон **консольного приложения рабочего процесса** .

1. Продолжайте создание проекта.

   > [!NOTE]
   > Если вы хотите добавить новый проект в существующее решение, откройте его в Visual Studio, щелкните правой кнопкой мыши решение в **Обозреватель решений** и выберите команду **Добавить**  >  **Новый проект**.

## <a name="workflow-console-app"></a>Консольное приложение рабочего процесса

Если выбрать шаблон **консольное приложение рабочего процесса** , Visual Studio создаст определение рабочего процесса в XAML. Откроется конструктор рабочих процессов и отобразится холст для созданного рабочего процесса. Чтобы составить рабочий процесс, перетащите действия или другие элементы рабочего процесса из **области элементов** в область конструктора.

## <a name="wcf-workflow-service-app"></a>Приложение службы рабочего процесса WCF

Если выбрать шаблон **приложения службы рабочего процесса WCF** , Visual Studio создаст определение службы как XAML. Конструктор рабочих процессов открывается в режиме конструктора с <xref:System.Activities.Statements.Sequence> действием, содержащим набор <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> действий и.

## <a name="activity-library"></a>Библиотека действий

Если выбрать шаблон **библиотеки действий** , Visual Studio создаст определение действия в XAML. Конструктор рабочих процессов откроется и отобразится холст для настраиваемого действия. Перетащите действие из **области элементов** в область конструктора, чтобы включить его в настраиваемое действие.

> [!NOTE]
> Вы можете использовать только одно дочернее действие в теле настраиваемого действия. Однако это дочернее действие может быть составным действием, например <xref:System.Activities.Statements.Sequence> действием или <xref:System.Activities.Statements.Flowchart> действием.

## <a name="activity-designer-library"></a>Библиотека конструктора действий

Если выбрать шаблон **библиотеки конструктора действий** , Visual Studio создаст определение конструктора действий в XAML и файл реализации кода программной части. Откроется конструктор рабочих процессов и отобразится холст для конструктора действий. Перетащите элемент управления Windows Presentation Foundation (WPF) из **области элементов** в область конструктора, чтобы использовать их в конструкторе настраиваемых действий.

Пример реализации пользовательского конструктора действий см. [в разделе как создать настраиваемый конструктор действий](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Конструкторы настраиваемых действий можно использовать для настраиваемых действий и действий .NET по умолчанию.

## <a name="see-also"></a>См. также раздел

- [Использование конструктора рабочих процессов](developing-applications-with-the-workflow-designer.md)
- [Разработка рабочих процессов (платформа .NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)
