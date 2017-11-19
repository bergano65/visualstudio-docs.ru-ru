---
title: "Как: Добавление дескриптора фильтра в метод Finder | Документы Microsoft"
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
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
ms.assetid: 228a6190-8cb8-4182-b6d9-d4c656f4a164
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 37aff0510af501b75aafe190fc412a0d4b9fd625
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Практическое руководство. Добавление дескриптора фильтра в метод Finder
  Дескрипторы фильтра позволяют пользователям модели для передачи значений методам перед их выполнением. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Одним из типичных сценариев является пользователей SharePoint для извлечения экземпляров внешнего типа контента, соответствующих некоторым условиям. Этот сценарий можно поддерживать путем добавления дескриптора фильтра в метод поиска.  
  
### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Добавление дескриптора фильтра в метод поиска  
  
1.  В **Подробности метода BDC** окна, разверните узел метода поиска, затем **параметры** узел, а затем добавьте входной параметр. Дополнительные сведения см. в разделе [как: Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  В **сведения о методе** окно, выберите дескриптор типа параметра.  
  
3.  В строке меню выберите **представление**, **окно свойств**.  
  
4.  В **свойства** задайте **имя типа** свойство с типом данных, который подходит для фильтра.  
  
     Например фильтр может использовать дату заказа для ограничения количества заказов, возвращаемых методом. Для поддержки данного фильтра **имя типа** свойства дескриптора типа должно быть присвоено **System.DateTime**.  
  
5.  В **сведения о методе** окна, разверните **дескрипторы фильтров** узла.  
  
6.  В **Добавление дескриптора фильтра** выберите **создать дескриптор фильтра**.  
  
     Новый дескриптор фильтра отображается под **дескрипторы фильтров** узла.  
  
7.  В строке меню выберите **представление**, **окно свойств**.  
  
8.  В **свойства** окно, выберите **тип** свойства.  
  
9. В списке, который отображается для **тип** свойства, выберите требуемый шаблон фильтрации.  
  
     Например, чтобы создать фильтр, использующий дату заказа для ограничения количества заказов, возвращенных в метод поиска, выберите **сравнения**. Фильтр сравнения гарантирует, что метод поиска возвращает только те экземпляры, которые удовлетворяют определенному условию. Дополнительные сведения о каждом шаблоне фильтрации см. в разделе [типы из фильтров, поддерживаемые BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. В **свойства** окно, выберите **связанные дескрипторы типа** свойство.  
  
11. В списке, который отображается для **связанные дескрипторы типа** свойства, выберите дескриптор типа, созданный ранее в этой процедуре. Это связывает фильтр входной параметр метода поиска.  
  
12. Добавьте код в метод поиска, который возвращает данные. Входной параметр можно использовать в качестве условия в запросе select.  
  
     В следующем примере возвращается заказов на продажу с указанной даты заказа.  
  
    > [!NOTE]  
    >  Замените значение `ServerName` поле с именем сервера.  
  
     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]  
  
## <a name="see-also"></a>См. также  
 [Как: Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Как: Добавление конкретного метода поиска](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Как: Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Как: определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  