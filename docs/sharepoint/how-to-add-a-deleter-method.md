---
title: Практическое руководство. Добавление метода Deleter | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d7a486ea4a448cb30b64631589f003854e8b1b40
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644397"
---
# <a name="how-to-add-a-deleter-method"></a>Практическое руководство. Добавление метода Deleter
  Вы можете включить конечный пользователь мог удалить запись данных из внешнего списка на сайте SharePoint, добавив метод удаления для модели. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-deleter-method"></a>Чтобы создать метод удаления

1. На **конструкторе BDC**, выберите сущность.

2. В строке меню выберите **представление** > **Other Windows** > **Подробности метода BDC**.

    **Подробности метода BDC** откроется окно. Дополнительные сведения об этом окне см. в разделе [Обзор средства конструирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. В **добавьте метод** выберите **создать метод удаления**.

    Visual Studio добавляет следующие элементы модели. Эти элементы появляются в **Подробности метода BDC** окна.

   - Метод с именем **удалить**.

   - Входной параметр для метода.

   - Дескриптор типа для параметра.

   - Экземпляр метода для метода.

     Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

4. В **обозревателе решений**, откройте контекстное меню файла кода службы, созданный для сущности и затем выберите **Просмотр кода**.

    В редакторе кода открывается файл кода службы сущности. Дополнительные сведения о файле код службы сущности, см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Добавьте код в метод удаления для удаления записи. В следующем примере удаляется элемент строки из заказа на продажу с помощью образца базы данных AdventureWorks для SQL Server.

   > [!NOTE]
   >  Данный метод в этом примере использует два входных параметра.

   > [!NOTE]
   >  Замените значение `ServerName` поле с именем сервера.

    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]

## <a name="see-also"></a>См. также
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Практическое руководство. Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Практическое руководство. Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Практическое руководство. Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)
