---
title: Как добавить действия на панель элементов (прежние версии) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3f982372f0189871c4f3d294c07a9e3cfc44391
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656619"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Как добавить действия в область элементов (для прежних версий)
При создании решения рабочего процесса с устаревшим компонентом [!INCLUDE[wfd1](../includes/wfd1-md.md)] , предназначенным для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] , пользовательские действия можно добавить в проект рабочего процесса и их конструкторы, размещенные на **панели элементов** для удобного доступа. Вы также можете добавлять действия непосредственно в **область элементов** из библиотеки динамической КОМПОНОВКИ (DLL).

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Добавление действия на панель элементов из библиотеки DLL

1. Щелкните правой кнопкой мыши область окна Область элементов в разделе **Рабочий процесс Windows**и выберите пункт **выбрать элементы**.

2. В диалоговом окне **Выбор элементов панели элементов** перейдите на вкладку **компоненты System. activitys** и нажмите кнопку **Обзор** в нижней правой части окна.

3. Выберите библиотеку DLL из каталога файлов, который содержит реализацию настраиваемого действия, добавляемого на **панель элементов**, а затем нажмите кнопку **Открыть**.

4. Нажмите кнопку **ОК** , чтобы завершить добавление действия на панель элементов.

## <a name="see-also"></a>См. также:
 Использование [устаревших действий рабочего процесса](../workflow-designer/legacy-workflow-activities.md) [в конструкторе устаревших действий](../workflow-designer/using-the-legacy-activity-designer.md)