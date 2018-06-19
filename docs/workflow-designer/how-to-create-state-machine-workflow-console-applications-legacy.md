---
title: 'Конструктор рабочих процессов - как: Создание консольного приложения рабочего процесса конечного автомата (для прежних версий)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- console applications, state machine workflows
- state machine workflow console applications
- state machine workflows, console applicationa
ms.assetid: d6170b5d-5d4f-48e1-8257-c78604f27eac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 805b048a9e30f7a637e178d223b962259dadd926
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971353"
---
# <a name="how-to-create-state-machine-workflow-console-applications-legacy"></a>Как создать консольные приложения рабочих процессов конечных автоматов (для прежних версий)

Выполните следующие действия для создания проекта консольного приложения рабочего процесса состояния компьютера с помощью старого, предусмотренные в конструкторе рабочих процессов Windows в Visual Studio 2010. Используйте конструктор рабочих процессов прежних версий, для целевой платформы .NET Framework 3.5 или WinFX.

## <a name="to-create-a-state-machine-application-project"></a>Создание проекта приложения конечного автомата

1.  Запустите Visual Studio.

2.  В меню **Файл** наведите указатель мыши на элемент **Создать** и выберите **Проект**.

     Откроется диалоговое окно **Новый проект** .

3.  Выберите либо **.NET Framework 3.0** параметр или **.NET Framework 3.5** вариант в раскрывающемся списке в верхней части **новый проект** окно, чтобы открыть конструктор прежних версий.

    > [!NOTE]
    > Значение по умолчанию в Visual Studio 2010 — **.NET Framework 4**. Этот параметр используется для создания приложений Windows Workflow Foundation (WF), предназначенных для .NET Framework 4 и не использует конструктор прежних версий.

4.  В **типы проектов** области, выберите Visual C# или Visual Basic (в разделе **другие языки**), а затем выберите **рабочего процесса**.

5.  В **шаблоны** выберите **консольное приложение рабочего процесса состояние машины**.

6.  В **имя** введите описательное имя проекта облегчить его определение.

7.  В **расположение** введите каталог, в котором требуется сохранить проект, или **Обзор** для перехода к нему.

     Если требуется создать для проекта каталог решения, выберите **создать каталог для решения** флажок и введите имя в **имя решения** поле.

8.  Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

- [Создание проектов рабочих процессов для прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)
- [Как создать библиотеку рабочих процессов конечного автомата (для прежних версий)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)