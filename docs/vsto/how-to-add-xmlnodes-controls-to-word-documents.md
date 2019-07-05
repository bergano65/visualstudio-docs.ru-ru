---
title: Практическое руководство. Добавление элементов управления XMLNodes в документы Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b54a341cd9dd949f892537ee384afb4984aecc02
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419693"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>Практическое руководство. Добавление элементов управления XMLNodes в документы Word
  **Важные** сведения, изложенные в этом разделе, касающиеся Microsoft Word, представленных исключительно для преимущество и лиц и организаций, расположенных за пределами США и их территорий или использующие или разработки программ, выполняемых на, продукты Microsoft Word, лицензированные корпорацией Майкрософт до января 2010 г, при удалении реализация конкретной функции в Microsoft связана с пользовательским XML-из Microsoft Word. Эти сведения, касающиеся Microsoft Word может не читают или используют отдельным лицам или организациям в Соединенных Штатах Америки или их территориях, которые используете, или разработке программ, выполняемых на продукты Microsoft Word, лицензированные корпорацией Майкрософт, начиная с 10 января 2010 г. ; Эти продукты, будет вести себя так же, как продукты до этой даты или приобретенных и лицензируются для использования за пределами США.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 При сопоставлении повторяющегося элемента схемы XML в документ Microsoft Office Word, Visual Studio автоматически добавляет <xref:Microsoft.Office.Tools.Word.XMLNodes> элемента управления в документ.

 Сведения о сопоставлении неповторяющихся элементов схемы XML, см. в разделе [как: Добавление элементов управления XMLNode в документы Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

> [!NOTE]
> <xref:Microsoft.Office.Tools.Word.XMLNodes> Управления не доступен из **элементов** или **источников данных** окна, а также могут создаваться программным способом.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnodes-control-to-a-document"></a>Чтобы добавить элемент управления XMLNodes в документ

1. В документ в конструкторе Visual Studio, на ленте щелкните **разработчика** вкладки.

    > [!NOTE]
    > Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [Как Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

2. В **XML** щелкните **схемы**.

     **Шаблоны и надстройки** откроется диалоговое окно.

3. Нажмите кнопку **схемы XML** вкладки.

4. Нажмите кнопку **добавить схему**.

     **Добавление схемы** откроется диалоговое окно.

5. Выберите схему XML, который содержит повторяющиеся элементы схемы и нажмите кнопку **откройте**.

     **Параметры схемы** откроется диалоговое окно.

6. Назначить псевдоним, или нажмите кнопку **ОК** Чтобы добавить эту схему без псевдонима.

     Схема добавляется в **Добавление схемы** диалоговое окно.

7. В **Добавление схемы** диалоговом окне щелкните **ОК**.

     **XML-структуру** откроется панель задач.

8. Щелкните повторяющегося элемента схемы **XML-структуру** область задач, чтобы добавить его в документ.

     <xref:Microsoft.Office.Tools.Word.XMLNodes> Создается и добавляется в проект элемента управления.

## <a name="see-also"></a>См. также
- [Элемент управления XMLNodes](../vsto/xmlnodes-control.md)
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
