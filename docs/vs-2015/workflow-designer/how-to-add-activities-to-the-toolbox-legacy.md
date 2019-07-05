---
title: Практическое руководство. Добавление действий на панель инструментов (для прежних версий) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c3a8c6f397bbafdbdb29ecbb193c4200a26335c3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943372"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Практическое руководство. Добавление действий в область элементов (для прежних версий)
При построении решения рабочего процесса с помощью прежних версий [!INCLUDE[wfd1](../includes/wfd1-md.md)] излюбленного [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], пользовательские действия можно добавить в проект рабочего процесса и размещать их конструкторы в **элементов** для простой доступ. Вы можете также добавить действия непосредственно к **элементов** из библиотеки динамической компоновки (DLL).  
  
### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Добавление действия на панель элементов из библиотеки DLL  
  
1. Щелкните правой кнопкой мыши поверхность окна панели элементов под **рабочего процесса Windows**, а затем нажмите кнопку **Выбор элементов**.  
  
2. В **Выбор элементов панели элементов** диалоговом окне щелкните **компоненты System.Activities** , а затем щелкните **Обзор** в нижней правой части окна.  
  
3. Выберите библиотеку DLL из каталога файла, который содержит реализацию пользовательского действия, чтобы добавить **элементов**, а затем нажмите кнопку **откройте**.  
  
4. Нажмите кнопку **ОК** чтобы завершить добавление действия на панель элементов.  
  
## <a name="see-also"></a>См. также  
 [Использование конструктора действия для прежних версий](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)