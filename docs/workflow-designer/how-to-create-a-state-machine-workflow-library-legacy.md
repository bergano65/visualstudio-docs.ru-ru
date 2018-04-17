---
title: 'Как: Создание библиотеки рабочего процесса конечного автомата (для прежних версий) | Документы Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a8220c6e9dbd2d97e0bf1017498ca3b295424863
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Как создать библиотеку рабочих процессов конечного автомата (для прежних версий)

Выполните следующие действия для создания проекта библиотеки рабочего процесса автомата конструкторе рабочих процессов прежних версий Windows, предоставляемые с помощью [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

### <a name="to-create-a-state-machine-workflow-library-project"></a>Создание проекта библиотеки рабочего процесса конечного автомата.

1.  Запустите Visual Studio.

2.  В меню **Файл** наведите указатель мыши на элемент **Создать** и выберите **Проект**.

     Откроется диалоговое окно **Новый проект** .

3.  Выберите либо **.NET Framework 3.0** параметр или **.NET Framework 3.5** вариант в раскрывающемся списке в верхней части **новый проект** окно, чтобы открыть конструктор прежних версий.

    > [!NOTE]
    > Параметр по умолчанию в [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] — **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], работающих на платформе [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)], и не использует конструктор прежних версий.

4.  В **типы проектов** области, выберите Visual C# или Visual Basic (в разделе **другие языки**), а затем выберите **рабочего процесса**.

5.  В **шаблоны** выберите **библиотеки рабочего процесса автомата**.

6.  В **имя** введите описательное имя проекта облегчить его определение.

7.  В **расположение** введите каталог, в котором требуется сохранить проект, или **Обзор** для перехода к нему.

     Если требуется создать для проекта каталог решения, выберите **создать каталог для решения** флажок и введите имя в **имя решения** поле.

8.  Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

- [Создание проектов рабочих процессов для прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)
- [Рабочие процессы конечного автомата](/dotnet/framework/windows-workflow-foundation/state-machine-workflows)