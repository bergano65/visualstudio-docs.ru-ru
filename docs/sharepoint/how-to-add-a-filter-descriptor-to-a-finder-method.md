---
title: Как добавить дескриптор фильтра в метод Finder | Документация Майкрософт
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
ms.openlocfilehash: f9dd853142d970cd14de20f4782accb3ce3e17eb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986251"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Как добавить дескриптор фильтра в метод Finder
  Дескрипторы фильтров позволяют потребителям модели передавать значения методам перед их выполнением. Дополнительные сведения см. [в разделе Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

 Один из распространенных сценариев заключается в том, что пользователи в SharePoint хотят получить экземпляры внешнего типа содержимого, соответствующие некоторым критериям. Этот сценарий можно обеспечить, добавив дескриптор фильтра в метод поиска.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Добавление дескриптора фильтра в метод Finder

1. В окне **сведения о методе BDC** разверните узел метода поиска, разверните узел **Параметры** , а затем добавьте входной параметр. Дополнительные сведения см. в разделе [инструкции. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2. В окне **сведения о методе** выберите дескриптор типа параметра.

3. В строке меню выберите **вид** > **Свойства окно**.

4. В окне **Свойства** задайте для свойства **имя типа** тип данных, подходящий для фильтра.

     Например, фильтр может использовать дату заказа для ограничения количества заказов на продажу, возвращаемых методом. Для поддержки этого фильтра свойство **имени типа** дескриптора типа должно иметь значение **System. DateTime**.

5. В окне **сведения о методе** разверните узел **дескрипторы фильтра** .

6. В списке **Добавить дескриптор фильтра** выберите **создать дескриптор фильтра**.

     Под узлом **дескрипторы фильтра** появится новый дескриптор фильтра.

7. В строке меню выберите **вид** > **Свойства окно**.

8. В окне **Свойства** выберите свойство **тип** .

9. В списке, который отображается для свойства **тип** , выберите нужный шаблон фильтрации.

     Например, чтобы создать фильтр, использующий дату заказа для ограничения количества заказов на продажу, возвращаемых в методе поиска, выберите **Сравнение**. Фильтр сравнения гарантирует, что метод поиска возвращает только те экземпляры, которые соответствуют определенному условию. Дополнительные сведения о каждом шаблоне фильтрации см. [в разделе Типы фильтров, ПОДДЕРЖИВАЕМЫХ BDC](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

10. В окне **Свойства** выберите **связанное свойство дескрипторов типа** .

11. В списке, который отображается для **соответствующего свойства дескрипторов типа** , выберите дескриптор типа, созданный ранее в этой процедуре. Это связывает фильтр с входным параметром метода поиска.

12. Добавьте код в метод Finder, который возвращает данные. Входной параметр можно использовать в качестве условия в запросе SELECT.

     В следующем примере возвращаются заказы на продажу, которые имеют указанную дату заказа.

    > [!NOTE]
    > Замените значение поля `ServerName` именем сервера.

     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]

## <a name="see-also"></a>См. также
- [Как добавить метод Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Как добавить конкретный метод поиска](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Как добавить параметр в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Как определить дескриптор типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
