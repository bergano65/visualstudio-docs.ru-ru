---
title: "Как: Добавление элементов управления XMLNode в документы Word | Документы Microsoft"
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
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
ms.assetid: d583b9d4-bd13-46e3-9eb7-da18fcb7eb8c
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a24f5b4205a558e950a7fe941ac6f8a3e7c45068
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Практическое руководство. Добавление элементов управления XMLNode в документы Word
  **Важные** сведения, изложенные в этом разделе, относящаяся к Microsoft Word, представленному исключительно для удобства и лиц и организаций, расположенных за пределами США и их территорий или с помощью или разработки программы, работающие на, продуктов Microsoft Word, лицензированные корпорацией Майкрософт до января 2010 года, когда Microsoft удален реализация конкретной функции, относящиеся к пользовательской XML из Microsoft Word. Эта информация, относящаяся к Microsoft Word нельзя прочитать или используемых отдельным лицам или организациям в Соединенных Штатах Америки или их территориях, которые используете или разработке программ, выполняемых на продукты Microsoft Word, лицензированные корпорацией Майкрософт после 10 января 2010 г. ; Эти продукты будут вести себя таким же, как продукты лицензированных до указанной даты или приобретенных и лицензированных за пределами США.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 При сопоставлении неповторяющегося элемента схемы XML в документ Microsoft Office Word, Visual Studio автоматически добавляет <xref:Microsoft.Office.Tools.Word.XMLNode> элемент управления. Сведения о сопоставлении повторяющихся элементов схем XML см. в разделе [как: Добавление элементов управления XMLNodes в документы Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNode> Управления не доступен из **элементов** или **источники данных** окна, который может быть создан программными средствами.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnode-control-to-a-document"></a>Чтобы добавить элемент управления XMLNode в документ  
  
1.  В документ в конструкторе Visual Studio на ленте щелкните **разработчика** вкладки.  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  В **XML** щелкните **схемы**.  
  
     **Шаблоны и надстройки** откроется диалоговое окно.  
  
3.  Нажмите кнопку **XML-схема** вкладки.  
  
4.  Нажмите кнопку **добавить схему**.  
  
     **Добавить схему** откроется диалоговое окно.  
  
5.  Выберите схему XML, который содержит повторяющиеся элементы схемы из **добавить схему** диалоговое окно и нажмите кнопку **откройте**.  
  
     **Параметры схемы** откроется диалоговое окно.  
  
6.  Укажите псевдоним или нажмите кнопку **ОК** для добавления схемы без псевдонима.  
  
     Схема добавляется к **добавить схему** диалоговое окно.  
  
7.  В **добавить схему** диалоговое окно, нажмите кнопку **ОК**.  
  
8.  **XML-структуру** откроется панель задач.  
  
9. Щелкните элемент схемы неповторяющихся **XML-структуру** область задач, чтобы добавить его в документ.  
  
     <xref:Microsoft.Office.Tools.Word.XMLNode> Создается и добавляется в проект элемента управления.  
  
## <a name="see-also"></a>См. также  
 [XMLNode-элемент управления](../vsto/xmlnode-control.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  