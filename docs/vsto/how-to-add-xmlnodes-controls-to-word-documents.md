---
title: "Как: Добавление элементов управления XMLNodes в документы Word | Документы Microsoft"
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
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c6410f3bdb1f74ce935715260572cbd17d4670c2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>Практическое руководство. Добавление элементов управления XMLNodes в документы Word
  **Важные** сведения, изложенные в этом разделе, относящаяся к Microsoft Word, представленному исключительно для удобства и лиц и организаций, расположенных за пределами США и их территорий или с помощью или разработки программы, работающие на, продуктов Microsoft Word, лицензированные корпорацией Майкрософт до января 2010 года, когда Microsoft удален реализация конкретной функции, относящиеся к пользовательской XML из Microsoft Word. Эта информация, относящаяся к Microsoft Word нельзя прочитать или используемых отдельным лицам или организациям в Соединенных Штатах Америки или их территориях, которые используете или разработке программ, выполняемых на продукты Microsoft Word, лицензированные корпорацией Майкрософт после 10 января 2010 г. ; Эти продукты будут вести себя таким же, как продукты лицензированных до указанной даты или приобретенных и лицензированных за пределами США.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 При сопоставлении повторяющегося элемента схемы XML в документ Microsoft Office Word, Visual Studio автоматически добавляет <xref:Microsoft.Office.Tools.Word.XMLNodes> элемент управления.  
  
 Сведения о сопоставлении неповторяющихся элементов схем XML см. в разделе [как: Добавление элементов управления XMLNode в документы Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNodes> Управления не доступен из **элементов** или **источники данных** окна, а также могут создаваться программным путем.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnodes-control-to-a-document"></a>Чтобы добавить элемент управления XMLNodes в документ  
  
1.  В документ в конструкторе Visual Studio на ленте щелкните **разработчика** вкладки.  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  В **XML** щелкните **схемы**.  
  
     **Шаблоны и надстройки** откроется диалоговое окно.  
  
3.  Нажмите кнопку **XML-схема** вкладки.  
  
4.  Нажмите кнопку **добавить схему**.  
  
     **Добавить схему** откроется диалоговое окно.  
  
5.  Выберите схему XML, который содержит повторяющиеся элементы схемы и нажмите кнопку **откройте**.  
  
     **Параметры схемы** откроется диалоговое окно.  
  
6.  Укажите псевдоним или нажмите кнопку **ОК** для добавления схемы без псевдонима.  
  
     Схема добавляется к **добавить схему** диалоговое окно.  
  
7.  В **добавить схему** диалоговое окно, нажмите кнопку **ОК**.  
  
     **XML-структуру** откроется панель задач.  
  
8.  Щелкните повторяющегося элемента схемы **XML-структуру** область задач, чтобы добавить его в документ.  
  
     <xref:Microsoft.Office.Tools.Word.XMLNodes> Создается и добавляется в проект элемента управления.  
  
## <a name="see-also"></a>См. также  
 [XMLNodes-элемент управления](../vsto/xmlnodes-control.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  