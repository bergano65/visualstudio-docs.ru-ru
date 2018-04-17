---
title: 'Как: Добавление элементов управления XMLNode в документы Word | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4dd214262f66bfa21cdb168e948c70437487761e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [Практическое руководство. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
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
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  