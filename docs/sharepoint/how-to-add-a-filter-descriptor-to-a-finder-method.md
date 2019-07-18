---
title: Практическое руководство. Добавление дескриптора фильтра в метод Finder | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fceb6270aea9da5af1a53adf7560df7dd3702349
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418309"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Практическое руководство. Добавление дескриптора фильтра в метод Finder
  Дескрипторы фильтров позволяет потребителям модели для передачи значений в методы, перед их выполнением. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

 Одним из типичных сценариев является пользователей в SharePoint для извлечения экземпляров внешнего типа содержимого, которые отвечают некоторым условиям. Этот сценарий можно поддерживать путем добавления дескриптора фильтра в метод Finder.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Добавление дескриптора фильтра в метод Finder

1. В **Подробности метода BDC** окне разверните узел метода поиска, затем **параметры** узел, а затем добавьте входной параметр. Дополнительные сведения см. в разделе [Как Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2. В **сведения о методе** окно, выберите дескриптор типа параметра.

3. В строке меню выберите **представление** > **окно "Свойства"**.

4. В **свойства** окне **имя типа** свойство с типом данных, который подходит для фильтра.

     Предположим, например фильтр использует дату заказа для ограничения количества заказов на продажу, возвращаемый методом. Для поддержки данного фильтра **имя типа** свойства дескриптора типа должно быть присвоено **System.DateTime**.

5. В **сведения о методе** окне разверните **дескриптора фильтра** узла.

6. В **Добавление дескриптора фильтра** выберите **создать дескриптор фильтра**.

     Новый дескриптор фильтра отображается под **дескриптора фильтра** узла.

7. В строке меню выберите **представление** > **окно "Свойства"**.

8. В **свойства** окно, выберите **тип** свойства.

9. В списке, который отображается для **тип** свойства, выберите нужный шаблон фильтрации.

     Например, чтобы создать фильтр, использующий дату заказа, чтобы ограничить количество заказов на продажу, возвращаемое в метод поиска, выберите **сравнения**. Фильтр сравнения гарантирует, что метод поиска возвращает только экземпляры, которые удовлетворяют определенному условию. Дополнительные сведения о каждом шаблоне фильтрации см. в разделе [Types of Filters Supported с BDC](http://go.microsoft.com/fwlink/?LinkId=169287).

10. В **свойства** окно, выберите **связанные дескрипторы типа** свойство.

11. В списке, который отображается для **связанные дескрипторы типа** свойства, выберите дескриптор типа, созданный ранее в этой процедуре. Это связывает фильтр входному параметру метода поиска.

12. Добавьте код в метод поиска, который возвращает данные. Входной параметр можно использовать как условие в запросе select.

     В следующем примере возвращается заказы на продажу, датой указанного заказа.

    > [!NOTE]
    > Замените значение `ServerName` поле с именем сервера.

     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]

## <a name="see-also"></a>См. также
- [Практическое руководство. Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Практическое руководство. Определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
