---
title: Как выполнить Добавление элементов управления XMLNode в документы Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: e0b3f4970dd1699efe000a67970f03629bef48a8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838915"
---
# <a name="how-to-add-xmlnode-controls-to-word-documents"></a>Как выполнить Добавление элементов управления XMLNode в документы Word
  **Важные** сведения, изложенные в этом разделе, касающиеся Microsoft Word, представленных исключительно для преимущество и лиц и организаций, расположенных за пределами США и их территорий или использующие или разработки программ, выполняемых на, продукты Microsoft Word, лицензированные корпорацией Майкрософт до января 2010 г, при удалении реализация конкретной функции в Microsoft связана с пользовательским XML-из Microsoft Word. Эти сведения, касающиеся Microsoft Word может не читают или используют отдельным лицам или организациям в Соединенных Штатах Америки или их территориях, которые используете, или разработке программ, выполняемых на продукты Microsoft Word, лицензированные корпорацией Майкрософт, начиная с 10 января 2010 г. ; Эти продукты, будет вести себя так же, как продукты до этой даты или приобретенных и лицензируются для использования за пределами США.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 При сопоставлении неповторяющегося элемента схемы XML в документ Microsoft Office Word, Visual Studio автоматически добавляет <xref:Microsoft.Office.Tools.Word.XMLNode> элемента управления в документ. Сведения о сопоставлении повторяющихся элементов схемы XML, см. в разделе [как: Добавление элементов управления XMLNodes в документы Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Word.XMLNode> Управления не доступен из **элементов** или **источников данных** окна, который может быть создан программными средствами.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-an-xmlnode-control-to-a-document"></a>Чтобы добавить элемент управления XMLNode в документ  
  
1.  В документ в конструкторе Visual Studio, на ленте щелкните **разработчика** вкладки.  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [Как Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  В **XML** щелкните **схемы**.  
  
     **Шаблоны и надстройки** откроется диалоговое окно.  
  
3.  Нажмите кнопку **схемы XML** вкладки.  
  
4.  Нажмите кнопку **добавить схему**.  
  
     **Добавление схемы** откроется диалоговое окно.  
  
5.  Выберите схему XML, который содержит повторяющиеся элементы схемы из **Добавление схемы** диалоговое окно и нажмите кнопку **откройте**.  
  
     **Параметры схемы** откроется диалоговое окно.  
  
6.  Назначить псевдоним, или нажмите кнопку **ОК** Чтобы добавить эту схему без псевдонима.  
  
     Схема добавляется в **Добавление схемы** диалоговое окно.  
  
7.  В **Добавление схемы** диалоговом окне щелкните **ОК**.  
  
8.  **XML-структуру** откроется панель задач.  
  
9. Щелкните неповторяющийся элемент схемы на **XML-структуру** область задач, чтобы добавить его в документ.  
  
     <xref:Microsoft.Office.Tools.Word.XMLNode> Создается и добавляется в проект элемента управления.  
  
## <a name="see-also"></a>См. также  
 [Элемент управления XMLNode](../vsto/xmlnode-control.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
