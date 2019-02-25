---
title: Практическое руководство. Сопоставление схем и документов Word в Visual Studio
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 37cdbc07f5defe0c6f8d5613795d2a9c6142521f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644709"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Практическое руководство. Сопоставление схем и документов Word в Visual Studio
  **Важные** сведения, изложенные в этом разделе, касающиеся Microsoft Word, представленных исключительно для преимущество и лиц и организаций, расположенных за пределами США и их территорий или использующие или разработки программ, выполняемых на, продукты Microsoft Word, лицензированные корпорацией Майкрософт до января 2010 г, при удалении реализация конкретной функции в Microsoft связана с пользовательским XML-из Microsoft Word. Эти сведения, касающиеся Microsoft Word может не читают или используют отдельным лицам или организациям в Соединенных Штатах Америки или их территориях, которые используете, или разработке программ, выполняемых на продукты Microsoft Word, лицензированные корпорацией Майкрософт, начиная с 10 января 2010 г. ; Эти продукты, будет вести себя так же, как продукты до этой даты или приобретенных и лицензируются для использования за пределами США.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Можно сопоставить схему XML в документ, когда документ открыт в среде Visual Studio. Можно использовать те же средства Microsoft Office Word, которые используются, если документ открыт вне Visual Studio. Проект Office создает те же объекты ли сопоставление с документом до или после создания решения Word.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Для сопоставления схемы XML в документ Word в Visual Studio

1.  Откройте проект документа или шаблона Word в Visual Studio.

2.  Щелкните в документе, чтобы переместить фокус в конструктор.

3.  На ленте щелкните **разработчика** вкладки.

    > [!NOTE]
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [Как Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4.  В **XML** щелкните **схемы**.

     **Шаблоны и надстройки** откроется диалоговое окно.

5.  Нажмите кнопку **схемы XML** вкладки.

6.  Нажмите кнопку **добавить схему**.

     **Добавление схемы** откроется диалоговое окно.

7.  Перейдите к нужному файлу схемы, выберите его и нажмите кнопку **откройте**.

     **Параметры схемы** откроется диалоговое окно.

8.  Назначить псевдоним, или нажмите кнопку **ОК** Чтобы добавить эту схему без псевдонима.

9. Нажмите кнопку **ОК**.

     **XML-структуру** откроется окно.

10. Перетащите элементы с **XML-структуру** окно до знаков в документе, в которой будут создаваться соответствующие элементы управления.

## <a name="see-also"></a>См. также
- [Практическое руководство. Сопоставление схем и листов внутри Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [XML-схемы и данные в настройках уровня документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
