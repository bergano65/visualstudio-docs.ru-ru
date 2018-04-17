---
title: 'Как: Создание библиотеки последовательных рабочих процессов (для прежних версий) | Документы Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 49ef9bd788a98178250e8830786d6301816ff616
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>Как создать библиотеку последовательных рабочих процессов (для прежних версий)

Выполните следующие действия для создания проекта библиотеки последовательного рабочего процесса с помощью прежних версий конструктора рабочих процессов Windows, предоставляемые [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

### <a name="to-create-a-sequential-workflow-library-project"></a>Создание проекта библиотеки последовательных рабочих процессов

1.  Запустите Visual Studio.

2.  В меню **Файл** наведите указатель мыши на элемент **Создать** и выберите **Проект**.

     Откроется диалоговое окно **Новый проект** .

3.  Выберите либо **.NET Framework 3.0** параметр или **.NET Framework 3.5** вариант в раскрывающемся списке в верхней части **новый проект** окно, чтобы открыть конструктор прежних версий.

    > [!NOTE]
    > Параметр по умолчанию в [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] — **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], работающих на платформе [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)], и не использует конструктор прежних версий.

4.  В **типы проектов** области, выберите Visual C# или Visual Basic (в разделе **другие языки**), а затем выберите **рабочего процесса**.

5.  В **шаблоны** выберите **библиотека последовательных рабочих процессов**.

6.  В **имя** введите описательное имя проекта облегчить его определение.

7.  В **расположение** введите каталог, в котором требуется сохранить проект, или **Обзор** для перехода к нему.

     Если требуется создать для проекта каталог решения, выберите **создать каталог для решения** флажок и введите имя в **имя решения** поле.

8.  Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

- [Создание проектов рабочих процессов для прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)
- [Стили разработки рабочего процесса](http://msdn.microsoft.com/en-us/aacf4ec6-da05-4974-958a-974769dda739)