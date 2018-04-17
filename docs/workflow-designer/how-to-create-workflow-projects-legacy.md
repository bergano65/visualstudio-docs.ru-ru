---
title: 'Как: Создание проектов рабочих процессов (для прежних версий) | Документы Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca6fdbbd8a744c472c06fdefbdafce77679ec2c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-workflow-projects-legacy"></a>Как создавать проекты рабочих процессов (для прежних версий)
Выполните следующие шаги для создания проекта [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], ориентированного на [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]. Эта процедура использует конструктор прежних версий рабочего процесса Windows, предоставляемые [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

### <a name="to-create-a-workflow-project"></a>Создание проекта рабочего процесса

1.  Запустите [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)].

2.  В меню **Файл** наведите указатель мыши на элемент **Создать** и выберите **Проект**.

     Откроется диалоговое окно **Новый проект** .

3.  Выберите либо **.NET Framework 3.0** параметр или **.NET Framework 3.5** вариант в раскрывающемся списке в верхней части **новый проект** окно, чтобы открыть конструктор прежних версий.

    > [!NOTE]
    > Параметр по умолчанию в [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] — **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], работающих на платформе [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)], и не использует конструктор прежних версий.

4.  В **типы проектов** панели выберите проекты Visual C# или проекты Visual Basic, а затем выберите **рабочего процесса**.

5.  В **шаблоны** области, выберите один из установленных шаблонов проекта:

    -   Консольное приложение последовательного рабочего процесса

    -   Библиотека последовательных рабочих процессов

    -   Библиотека действий рабочих процессов

    -   Консольное приложение рабочего процесса конечного автомата

    -   Библиотека рабочих процессов конечного автомата

    -   Пустой проект рабочего процесса

6.  В **имя** введите описательное имя проекта облегчить его определение.

7.  В **расположение** введите каталог, в котором требуется сохранить проект, или **Обзор** для перехода в каталог.

     Если требуется создать для проекта каталог решения, выберите **создать каталог для решения** флажок и введите имя в **имя решения** поле.

8.  Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

- [Создание проектов рабочих процессов для прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)