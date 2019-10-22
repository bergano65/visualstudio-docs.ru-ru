---
title: Как создавать проекты рабочих процессов (прежние версии) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf68c1a28f662bfa4e271d3c402ef1c8946b6f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668680"
---
# <a name="how-to-create-workflow-projects-legacy"></a>Как создавать проекты рабочих процессов (для прежних версий)
Выполните следующие шаги для создания проекта [!INCLUDE[wf](../includes/wf-md.md)], ориентированного на [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]. В этой процедуре используется средство [!INCLUDE[wfd1](../includes/wfd1-md.md)] более ранней версии, поставляемое вместе с [!INCLUDE[vs2010](../includes/vs2010-md.md)].

### <a name="to-create-a-workflow-project"></a>Создание проекта рабочего процесса

1. Запустите [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)].

2. В меню **Файл** наведите указатель мыши на элемент **Создать** и выберите **Проект**.

     Откроется диалоговое окно **Новый проект** .

3. Выберите параметр **.NET Framework 3,0** или **.NET Framework 3,5** в раскрывающемся списке в верхней части окна **нового проекта** , чтобы получить доступ к конструктору прежних версий.

    > [!NOTE]
    > Параметр по умолчанию в [!INCLUDE[vs2010](../includes/vs2010-md.md)] имеет значение **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../includes/wf-md.md)], работающих на платформе [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], и не использует конструктор прежних версий.

4. В области **типы проектов** выберите визуальные C# проекты или проекты Visual Basic, а затем выберите **Рабочий процесс**.

5. В области **шаблоны** выберите один из установленных шаблонов проектов.

    - Консольное приложение последовательного рабочего процесса

    - Библиотека последовательных рабочих процессов

    - Библиотека действий рабочих процессов

    - Консольное приложение рабочего процесса конечного автомата

    - Библиотека рабочих процессов конечного автомата

    - Пустой проект рабочего процесса

6. В поле **имя** введите описательное имя проекта, чтобы упростить его поиск.

7. В поле **Расположение** введите каталог, в котором необходимо сохранить проект, или нажмите кнопку **Обзор** , чтобы перейти к каталогу.

     Если требуется создать каталог решения для проекта, установите флажок **создать каталог для решения** и введите имя в поле **имя решения** .

8. Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также раздел
 [Создание проектов рабочих процессов для прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)