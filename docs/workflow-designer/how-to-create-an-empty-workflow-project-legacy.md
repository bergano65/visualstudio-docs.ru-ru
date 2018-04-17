---
title: 'Как: создать пустой проект рабочего процесса (для прежних версий) | Документы Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects, empty workflow
- empty workflow projects
- workflows, empty workflow projects
ms.assetid: f81b9cf2-9adb-47a2-936b-cb1851614e19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 961425eb7f3b4d412ddcb572bc21a91bdde6e957
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-empty-workflow-project-legacy"></a>Как создать пустой проект рабочего процесса (для прежних версий)
Выполните следующие действия, чтобы создать пустой проект рабочего процесса с помощью прежних версий конструктора рабочих процессов Windows, предоставляемые [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

### <a name="to-create-an-empty-workflow-project"></a>Создание пустого проекта рабочего процесса

1.  Запустите Visual Studio.

2.  В меню **Файл** наведите указатель мыши на элемент **Создать** и выберите **Проект**.

     Откроется диалоговое окно **Новый проект** .

3.  Выберите либо **.NET Framework 3.0** параметр или **.NET Framework 3.5** вариант в раскрывающемся списке в верхней части **новый проект** окно, чтобы открыть конструктор прежних версий.

    > [!NOTE]
    > Параметр по умолчанию в [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] — **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], работающих на платформе [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)], и не использует конструктор прежних версий.

4.  В **типы проектов** области, выберите Visual C# или Visual Basic (в разделе **другие языки**), а затем выберите **рабочего процесса**.

5.  В **шаблоны** выберите **пустой проект рабочего процесса**.

6.  В **имя** введите описательное имя проекта облегчить его определение.

7.  В **расположение** введите каталог, в котором требуется сохранить проект, или **Обзор** для перехода к нему.

     Если требуется создать для проекта каталог решения, выберите **создать каталог для решения** флажок и введите имя в **имя решения** поле.

8.  Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

- [Создание проектов рабочих процессов для прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)