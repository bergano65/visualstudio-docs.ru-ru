---
title: 'Как: Добавление действий на панель инструментов (устаревшая версия) | Документы Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 779735cb1d163db9e7b05e2892d01a991a4a4c2c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Как добавить действия в область элементов (для прежних версий)
При построении решения рабочего процесса в конструкторе рабочих процессов прежних версий Windows, предназначенное [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], пользовательские действия можно добавить в проект рабочего процесса и размещать их конструкторы в **элементов** для простой доступ. Можно также добавить действия непосредственно в **элементов** из библиотеки динамической компоновки (DLL).

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Добавление действия на панель элементов из библиотеки DLL

1.  Щелкните правой кнопкой мыши поверхность окна панели элементов под **рабочего процесса Windows**, а затем нажмите кнопку **Выбор элементов**.

2.  В **Выбор элементов панели элементов** диалоговое окно, нажмите кнопку **System.Activities Components** , а затем щелкните **Обзор** из правой нижней части окна.

3.  Выберите библиотеку DLL из каталога файла, который содержит реализацию пользовательского действия, чтобы добавить **элементов**, а затем нажмите кнопку **откройте**.

4.  Нажмите кнопку **ОК** чтобы завершить добавление действия в область элементов.

## <a name="see-also"></a>См. также

- [Использование конструктора действия для прежних версий](../workflow-designer/using-the-legacy-activity-designer.md)
- [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)