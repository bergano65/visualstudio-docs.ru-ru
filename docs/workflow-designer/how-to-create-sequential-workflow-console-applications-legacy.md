---
title: 'Как: Создание консольного приложения последовательного рабочего процесса (для прежних версий) | Документы Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26b479fb5f926d6dff0e1db05fe36fc4354ec89d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Как создавать консольные приложения последовательных рабочих процессов (для прежних версий)
Выполните следующие действия для создания проекта консольного приложения последовательного рабочего процесса с помощью прежних версий конструктора рабочих процессов Windows, предоставляемые [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

### <a name="to-create-a-sequential-workflow-console-application"></a>Создание консольного приложения последовательного рабочего процесса

1.  Запустите Visual Studio.

2.  В меню **Файл** наведите указатель мыши на элемент **Создать** и выберите **Проект**.

     Откроется диалоговое окно **Новый проект** .

3.  Выберите либо **.NET Framework 3.0** параметр или **.NET Framework 3.5** вариант в раскрывающемся списке в верхней части **новый проект** окно, чтобы открыть конструктор прежних версий.

    > [!NOTE]
    > Параметр по умолчанию в [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] — **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], работающих на платформе [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)], и не использует конструктор прежних версий.

4.  В **типы проектов** области, выберите проекты Visual C# или проекты Visual Basic (в разделе **другие языки**), а затем выберите **рабочего процесса**.

5.  В **шаблоны** выберите **консольного приложения последовательного рабочего процесса**.

6.  В **имя** введите описательное имя проекта облегчить его определение.

7.  В **расположение** введите каталог, в котором требуется сохранить проект, или **Обзор** для перехода к нему.

     Откроется конструктор Windows Forms и отобразится форма Form1 созданного проекта.

8.  Нажмите кнопку **ОК**.

     Откроется конструктор рабочих процессов и отобразится рабочая область конструктора рабочих процессов созданного последовательного рабочего процесса.

9. Перетащите действие с **элементов** в область конструктора в **перетащите действие** назначенную область.

## <a name="see-also"></a>См. также

- [Создание проектов рабочих процессов для прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)
- [Разработка рабочих процессов](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)