---
title: 'Практическое: запустите мастер настройки TableAdapter | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, Configuration Wizard
- TableAdapter Configuration Wizard
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7f603789014239762f564c3b2391b99865d8f620
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261902"
---
# <a name="how-to-start-the-tableadapter-configuration-wizard"></a>Практическое руководство. Запуск мастера настройки адаптера таблицы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Мастер настройки адаптера таблицы** создает и изменяет адаптеры таблицы в строго типизированных наборов данных. Этот мастер создает адаптеры таблицы на основе вводимых вами в мастере инструкций SQL или существующих хранимых процедур в базе данных. Этот мастер может также создавать новые хранимые процедуры в базе данных на основе инструкций SQL, вводимых вами в мастере.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-create-a-new-tableadapter"></a>Запуск мастера настройки адаптера таблицы для создания нового адаптера таблицы  
  
1.  Откройте набор данных в **конструктор наборов данных**. Дополнительные сведения см. в разделе [как: Открытие набора данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
    > [!NOTE]
    >  Если у вас нет набора данных в проекте, см. в разделе [создать и настроить наборы данных](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
2.  Если вы создаете новый адаптер таблицы, перетащите **TableAdapter** объекта из **набора данных** вкладке **элементов** на **конструктор наборов данных**.  
  
3.  На **Выбор подключения к данным** странице, выберите подключение к данным из списка доступных подключений или выберите **новое подключение** для создания нового соединения.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-edit-an-existing-tableadapter"></a>Запуск мастера настройки адаптера таблицы для изменения существующего адаптера таблицы  
  
1.  Откройте набор данных в **конструктор наборов данных**. Дополнительные сведения см. в разделе [как: Открытие набора данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Щелкните правой кнопкой мыши TableAdapter в **конструктор наборов данных** и выберите **Настройка**. В мастере откроется **Создание инструкций SQL** страницы или **привязка команд к хранимым процедурам** страницы, в зависимости от способа первоначальной настройке адаптера.  
  
3.  Завершите работу мастера.  
  
## <a name="see-also"></a>См. также  
 [Примеры работы с данными](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Общие сведения о TableAdapter](../data-tools/tableadapter-overview.md)   
 [Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md)   
 [Добавление новых источников данных](../data-tools/add-new-data-sources.md)   
 [Практическое руководство. Подключение к данным в базе данных](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Практическое: сортировка и фильтрация данных ADO.NET с помощью компонента BindingSource в Windows Forms](http://msdn.microsoft.com/library/6c206daf-d706-4602-9dbe-435343052063)   
 [Практическое: создание таблицы подстановок с помощью компонента BindingSource в Windows Forms](http://msdn.microsoft.com/library/622fce80-879d-44be-abbf-8350ec22ca2b)   
 [Пошаговое руководство. Отображение данных на форме в приложении Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)