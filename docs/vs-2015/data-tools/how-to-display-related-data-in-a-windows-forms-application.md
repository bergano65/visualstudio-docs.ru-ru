---
title: 'Практическое: отображение связанных данных в Windows Forms Application | Документация Майкрософт'
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
- Windows Forms, displaying data
- displaying data, related data
- related data, displaying
- displaying tables, related data
- data [Windows Forms], displaying
- displaying table data
- data [Windows Forms], related
- displaying data on forms, related data
- displaying table information
ms.assetid: 60b1f1ec-6257-42ab-83f0-06d54ed364fd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3fd7a29e1de66a5b5fd57dab1adbcf99128001ac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215466"
---
# <a name="how-to-display-related-data-in-a-windows-forms-application"></a>Практическое руководство. Отображение связанных данные в приложении Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно отобразить связанные данные путем перетаскивания элементов, которые совместно используют один и тот же узел главной таблицы из [окна "Источники данных"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) на форму. Например, если у вас есть источник данных, который имеет `Customers` таблицы и связанный с ним `Orders` таблицы, вы увидите обе таблицы как узлы высшего уровня (в представлении в виде дерева) в **источников данных** окна. Разверните `Customers` узел, чтобы просмотреть столбцы, и вы заметите, что последний столбец в списке является расширяемым узлом представляющий `Orders` таблицы. Этот узел представляет связанные заказы для клиента. Это означает, что если вы хотите создать форму, которая позволяет выбрать клиента и затем отобразить список заказов этого клиента, перетащите элементы, которые требуется отобразить из этой одной иерархии.  
  
 ![Окно источников данных, показывающая связь](../data-tools/media/datasources2.gif "DataSources2")  
Создание элементов управления с привязкой к данным, отображающих связанные записи  
  
 ![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo") видеоверсию этого раздела, см. в разделе [How do I: обновление связанных таблиц](http://go.microsoft.com/fwlink/?LinkId=143527).  
  
### <a name="to-create-controls-that-display-related-records"></a>Для создания элементов управления, отображающих связанные записи  
  
1.  Откройте форму в [конструктор Windows Forms](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
2.  Откройте **источников данных** окна. Дополнительные сведения см. в разделе [как: Откройте окно "Источники данных"](../data-tools/how-to-open-the-data-sources-window.md).  
  
3.  Разверните узел, представляющий родительскую таблицу в отношении. (Родительская таблица является таблицей на стороне «один» отношения «один ко многим»).  
  
4.  Перетащите все элементы, которые требуется отобразить из родительской таблицы в связи с **источников данных** окна на форму.  
  
5.  Связанные дочерние таблицы отображаются в виде разворачиваемых узлов в нижней части списка столбцов родительской таблицы. Перетащите элементы, будет отображаться из таких связанных узлов на форму.  
  
    > [!NOTE]
    >  Перетаскивание элемента из узлов верхнего уровня создает отдельный несвязанных [компонент BindingSource](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9) , облегчает перемещение связанных записей. Для привязки связанных данных необходимо выбрать таблицы из одного иерархического узла.  
  
## <a name="see-also"></a>См. также  
 [Примеры работы с данными](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Пошаговое руководство: Отображение данных в форме Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Общие сведения о TableAdapter](../data-tools/tableadapter-overview.md)   
 [Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md)   
 [Добавление новых источников данных](../data-tools/add-new-data-sources.md)   
 [Практическое руководство. Подключение к данным в базе данных](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Практическое руководство. Переход между данными с помощью элемента управления BindingNavigator в Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)