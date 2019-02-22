---
title: Практическое руководство. Добавление метода Creator | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1c1596213b618ba67cd4bf1406f63c0754fd9b96
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619320"
---
# <a name="how-to-add-a-creator-method"></a>Практическое руководство. Добавление метода Creator
  Метод создания добавляет новые данные в источник данных сущности. Служба бизнес-данным (BDC) вызывает этот метод, при выборе пользователем **новый элемент** кнопку **ленты** списка, который основан на модели. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-add-a-creator-method"></a>Добавление метода Creator

1. На **конструкторе BDC**, выберите сущность.

2. В строке меню выберите **представление** > **Other Windows** >**Подробности метода BDC**.

    **Подробности метода BDC** откроется окно. Дополнительные сведения об этом окне см. в разделе [Обзор средства конструирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. В **добавьте метод** выберите **создать метод**.

    Visual Studio добавляет следующие элементы модели, и эти элементы появляются в **Подробности метода BDC** окна.

   - Метод с именем **создать**.

   - Входной параметр для метода.

   - Возвращаемый параметр для метода.

   - Дескрипторы для параметров типа.

   - Экземпляр метода для метода.

     Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

4. В **обозревателе решений**, откройте контекстное меню файла кода службы, созданный для сущности и затем выберите **Просмотр кода**.

    В редакторе кода открывается файл кода службы сущности. Дополнительные сведения о файле код службы сущности, см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Добавьте код в метод Creator, который добавляет данные к источнику данных. В следующем примере добавляется контакт с образцом базы данных AdventureWorks для SQL Server.

   > [!NOTE]
   >  Замените значение `ServerName` поле с именем сервера.

    [!code-csharp[SP_BDC#4](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#4)]
    [!code-vb[SP_BDC#4](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#4)]

## <a name="see-also"></a>См. также
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Практическое руководство. Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Практическое руководство. Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Практическое руководство. Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)
