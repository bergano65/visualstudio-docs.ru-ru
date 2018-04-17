---
title: 'Как: сопоставление схем в документы Word в Visual Studio | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 629149eab19dbd717cdc663a58a53659ae18a4af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Практическое руководство. Сопоставление схем и документов Word в Visual Studio
  **Важные** сведения, изложенные в этом разделе, относящаяся к Microsoft Word, представленному исключительно для удобства и лиц и организаций, расположенных за пределами США и их территорий или с помощью или разработки программы, работающие на, продуктов Microsoft Word, лицензированные корпорацией Майкрософт до января 2010 года, когда Microsoft удален реализация конкретной функции, относящиеся к пользовательской XML из Microsoft Word. Эта информация, относящаяся к Microsoft Word нельзя прочитать или используемых отдельным лицам или организациям в Соединенных Штатах Америки или их территориях, которые используете или разработке программ, выполняемых на продукты Microsoft Word, лицензированные корпорацией Майкрософт после 10 января 2010 г. ; Эти продукты будут вести себя таким же, как продукты лицензированных до указанной даты или приобретенных и лицензированных за пределами США.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 XML-схемы можно сопоставить с документом, когда документ открыт в Visual Studio. Можно использовать те же средства Microsoft Office Word, которые используются, если документ открыт вне Visual Studio. Проект Office создает те же объекты, является ли сопоставление с документом до или после создания решения Word.  
  
### <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Для сопоставления схемы XML в документ Word в Visual Studio  
  
1.  Откройте проект документа или шаблона Word в Visual Studio.  
  
2.  Щелкните в документе для перемещения фокуса в конструктор.  
  
3.  На ленте перейдите на вкладку **Разработчик** .  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [Практическое руководство. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  В **XML** щелкните **схемы**.  
  
     **Шаблоны и надстройки** откроется диалоговое окно.  
  
5.  Нажмите кнопку **XML-схема** вкладки.  
  
6.  Нажмите кнопку **добавить схему**.  
  
     **Добавить схему** откроется диалоговое окно.  
  
7.  Перейдите к нужному файлу схемы, выберите его и нажмите кнопку **откройте**.  
  
     **Параметры схемы** откроется диалоговое окно.  
  
8.  Укажите псевдоним или нажмите кнопку **ОК** для добавления схемы без псевдонима.  
  
9. Нажмите кнопку **ОК**.  
  
     **XML-структуру** открывается окно.  
  
10. Перетащите элементы из **XML-структуру** окна на части в документе, где необходимо создать соответствующие элементы управления.  
  
## <a name="see-also"></a>См. также  
 [Как: сопоставление схем и листов внутри Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [XML-схемы и данные в настройках на уровне документа](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  