---
title: Практическое руководство. Добавление метода Updater | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8204b13aa0405d01590e4aeb0fe43a92b41c226f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431264"
---
# <a name="how-to-add-an-updater-method"></a>Практическое руководство. Добавление метода Updater
  Можно разрешить пользователям обновлять бизнес-данные во внешнем списке SharePoint, создав *Updater* метод. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-an-updater-method"></a>Чтобы создать метод обновления

1. В конструкторе BDC выберите сущность.

2. В строке меню выберите **представление** > **Other Windows** > **Подробности метода BDC**.

    Откроется окно Подробности метода BDC. Дополнительные сведения об этом окне см. в разделе [Обзор средства конструирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. В **добавьте метод** выберите **создать метод обновления**.

    Visual Studio добавляет следующие элементы модели. Эти элементы появляются в окне Подробности метода BDC.

   - Метод, который называется **обновления**.

   - Входной параметр для метода.

   - Дескриптор типа для параметра. По умолчанию Visual Studio использует дескриптор типа сущности, которое было определено для метода поиска (например: Обратитесь в службу).

   - Экземпляр метода для метода.

     Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

   > [!NOTE]
   > Если идентификатор типа сущности представляет поле в таблицу базы данных, который создается автоматически, задайте **поле средства предобновления** свойства **True**.

4. В **обозревателе решений**, откройте контекстное меню файла кода службы, созданный для сущности и затем выберите **Просмотр кода**.

    Открывает файл кода службы сущности в **редактор кода**. Дополнительные сведения об этом файле см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Добавьте код к методу Update для обновления данных. В следующем примере обновляется сведения для контакта в образце базы данных AdventureWorks для SQL Server.

   > [!NOTE]
   > Замените значение `ServerName` поле с именем сервера.

    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]

## <a name="see-also"></a>См. также
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Практическое руководство. Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Практическое руководство. Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Практическое руководство. Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Практическое руководство. Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)
