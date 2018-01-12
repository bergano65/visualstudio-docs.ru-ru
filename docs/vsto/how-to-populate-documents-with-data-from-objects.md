---
title: "Как: Заполнение документов данными из объектов | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 02f2b735ceb473f7ffe55345c1cd45dc084edb80
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Практическое руководство. Заполнение документов данными из объектов
  Доступ к данным в объекте данных в проектах уровня документа Microsoft Office Word осуществляется точно так же, как в проектах Windows Forms. Для получения данных из объекта в решении можно использовать те же средства и компоненты кода. Также можно использовать элементы управления Windows Forms для отображения данных. Кроме того, данные можно показать с помощью элементов управления ведущего приложения. Элементы управления ведущего приложения представляют собой управляемые объекты Microsoft Office Word, дополненные событиями и функциями привязки данных. Для получения дополнительной информации см. [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Чтобы заполнить документ данными из объекта, необходимо выполнить три основных действия:  
  
-   добавить в документ элемент управления, который можно привязать к данным;  
  
-   добавить данные из объекта в документ;  
  
-   подключить объект данных к BindingSource.   
  
## <a name="adding-a-data-object"></a>Добавление объекта данных  
  
#### <a name="to-add-a-data-object"></a>Добавление объекта данных  
  
-   Откройте окно **Источники данных** и создайте источник данных из объекта. Дополнительные сведения см. в разделе [Добавление новых источников данных](/visualstudio/data-tools/add-new-data-sources).  
  
## <a name="connecting-the-data-object-to-the-bindingsource"></a>Подключение объекта данных к BindingSource  
 В проектах уровня документа вы добавляете элементы управления в документ и привязываете их к данным во время разработки.  
  
 В проектах надстроек VSTO вы создаете элементы управления и привязываете их во время выполнения.  
  
### <a name="document-level-projects"></a>Проекты уровня документа  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>Подключение объекта данных к BindingSource  
  
1.  Перетащите нужное поле данных из окна **Источники данных** в документ. При этом автоматически создается элемент управления.  
  
2.  Создайте в коде экземпляр типа объекта, выбранного в качестве источника данных.  
  
3.  Присвойте этот экземпляр свойству <xref:System.Windows.Forms.BindingSource.DataSource%2A> объекта <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="application-level-projects"></a>Проекты уровня приложения  
  
##### <a name="to-connect-the-data-object-to-the-bindingsource"></a>Подключение объекта данных к BindingSource  
  
1.  Создайте в коде экземпляр типа объекта, связанного с источником данных.  
  
2.  Создайте экземпляр класса <xref:System.Windows.Forms.BindingSource>.  
  
3.  Присвойте экземпляр источника данных свойству <xref:System.Windows.Forms.BindingSource.DataSource%2A> объекта <xref:System.Windows.Forms.BindingSource>.  
  
4.  Добавьте источник данных как привязку данных к элементу управления.  
  
## <a name="see-also"></a>См. также  
 
 [Добавление новых источников данных](/visualstudio/data-tools/add-new-data-sources)   
 [Привязка элементов управления Windows Forms к данным в Visual Stduio](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)
 
 [Как: Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Как: обновления источника данных с данными из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Подключение к данным в приложениях Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Общие сведения о компоненте BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)  
  
  