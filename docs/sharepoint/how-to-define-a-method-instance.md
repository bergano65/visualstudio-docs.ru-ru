---
title: Практическое руководство. Определение экземпляра метода | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2f879f8367ad1b992300c9e5b1c8a2887e89205b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608020"
---
# <a name="how-to-define-a-method-instance"></a>Практическое руководство. Определение экземпляра метода
  Необходимо определить хотя бы один экземпляр метода для каждого метода в модели.

 Добавление экземпляра метода с помощью **Подробности метода BDC** окна. При добавлении экземпляра метода, Visual Studio добавляет `<MethodInstance>` элемент к XML-файла модели в проекте. Дополнительные сведения об атрибутах `<MethodInstance>` элемент, см. в разделе [экземпляр метода](http://go.microsoft.com/fwlink/?LinkID=169282).

### <a name="to-define-a-method-instance"></a>Определение экземпляра метода

1.  В **Подробности метода BDC** окне разверните узел метода и раскройте **экземпляров** узла.

2.  В **Добавление экземпляра метода** выберите **создать экземпляр метода поиска**.

     Новый экземпляр метода появится под **экземпляров** узла.

3.  В строке меню выберите **представление** > **окно "Свойства"**.

4.  В **свойства** окна, задайте свойства экземпляра метода. Дополнительные сведения о каждом свойстве см. в разделе [экземпляр метода](http://go.microsoft.com/fwlink/?LinkID=169282).

## <a name="see-also"></a>См. также
- [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Практическое руководство. Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Практическое руководство. Определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
