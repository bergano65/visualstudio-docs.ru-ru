---
title: 'Практическое: изменение запросов TableAdapter | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DbSource
- vbdata.Microsoft.VSDesigner.DataSource.DbSource
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- queries [Visual Basic], editing
- TableAdapters, editing queries
- data [Visual Studio], TableAdapters
- editing queries
ms.assetid: aac7b7b4-bd91-4225-95d4-a07643568c43
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 687336b979ef7e6d46ea6deb4a5682f3aec065be
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287902"
---
# <a name="how-to-edit-tableadapter-queries"></a>Практическое руководство. Изменение запросов TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Изменение запросов TableAdapter с [редактирования TableAdapters](../data-tools/editing-tableadapters.md) в **конструктор наборов данных**. Следует изменить запроса адаптера таблицы, когда он больше не соответствует требованиям приложения. (Кроме того, можно создать дополнительные запросы в TableAdapter. Дополнительные сведения о добавлении новых запросов, см. в разделе [как: создание запросов TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).)  
  
> [!NOTE]
>  Если [мастер настройки адаптера таблицы](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) открывает вместо **мастер настройки запроса адаптера таблицы**, возможно, был выбран TableAdapter main `Fill` запроса, а не один из Дополнительные запросы адаптера таблицы. Для основные сведения об изменении TableAdapter `Fill` запроса, см. в разделе [как: изменить адаптеры таблицы](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
 ![TableAdapter с несколькими запросами](../data-tools/media/tableadapter.gif "адаптера таблицы")  
  
### <a name="to-edit-a-tableadapter-query"></a>Изменение запроса адаптера таблицы  
  
1.  Откройте набор данных в **конструктор наборов данных**. Дополнительные сведения см. в разделе [как: Открытие набора данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Выберите запрос TableAdapter, который требуется изменить.  
  
3.  Щелкните правой кнопкой мыши запрос TableAdapter и выберите **Настройка**.  
  
     **Мастер настройки запроса TableAdapter** откроется, вы сможете изменять запрос или хранимую процедуру для этого запроса.  
  
4.  Завершить **мастер настройки запроса TableAdapter** с нужными изменениями. Дополнительные сведения см. в разделе [редактирования TableAdapters](../data-tools/editing-tableadapters.md).  
  
## <a name="see-also"></a>См. также  
 [Адаптеры таблиц](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)   
 [Примеры работы с данными](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)