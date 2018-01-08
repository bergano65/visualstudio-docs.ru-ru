---
title: "Как: Добавление действий на панель инструментов (устаревшая версия) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: b7bc489c000cf2d5fa875859208aa631a839168d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Как добавить действия в область элементов (для прежних версий)
При построении решения рабочего процесса с унаследованными [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] , ориентированном [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], пользовательские действия можно добавить в проект рабочего процесса и размещать их конструкторы в **элементов** для простой доступ. Можно также добавить действия непосредственно в **элементов** из библиотеки динамической компоновки (DLL).  
  
### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Добавление действия на панель элементов из библиотеки DLL  
  
1.  Щелкните правой кнопкой мыши поверхность окна панели элементов под **рабочего процесса Windows**, а затем нажмите кнопку **Выбор элементов**.  
  
2.  В **Выбор элементов панели элементов** диалоговое окно, нажмите кнопку **System.Activities Components** , а затем щелкните **Обзор** из правой нижней части окна.  
  
3.  Выберите библиотеку DLL из каталога файла, который содержит реализацию пользовательского действия, чтобы добавить **элементов**, а затем нажмите кнопку **откройте**.  
  
4.  Нажмите кнопку **ОК** чтобы завершить добавление действия в область элементов.  
  
## <a name="see-also"></a>См. также  
 [Использование конструктора действий прежних версий](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)