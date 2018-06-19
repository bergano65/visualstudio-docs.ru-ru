---
title: 'Конструктор рабочих процессов - как: Добавление действий на панель инструментов (для прежних версий)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99a8e1cef2ff5ddd526133355c608fa5218573d1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969431"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Как добавить действия в область элементов (для прежних версий)

При построении решения рабочего процесса в конструкторе рабочих процессов прежних версий Windows, предназначенное для .NET Framework версии 3.5 или WinFX, пользовательские действия можно добавить в проект рабочего процесса и размещать их конструкторы в **элементов** для простой доступ. Можно также добавить действия непосредственно в **элементов** из библиотеки динамической компоновки (DLL).

## <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Добавление действия на панель элементов из библиотеки DLL

1.  Щелкните правой кнопкой мыши поверхность окна панели элементов под **рабочего процесса Windows**, а затем нажмите кнопку **Выбор элементов**.

2.  В **Выбор элементов панели элементов** диалоговое окно, нажмите кнопку **System.Activities Components** , а затем щелкните **Обзор** из правой нижней части окна.

3.  Выберите библиотеку DLL из каталога файла, который содержит реализацию пользовательского действия, чтобы добавить **элементов**, а затем нажмите кнопку **откройте**.

4.  Нажмите кнопку **ОК** чтобы завершить добавление действия в область элементов.

## <a name="see-also"></a>См. также

- [Использование конструктора действия для прежних версий](../workflow-designer/using-the-legacy-activity-designer.md)
- [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)