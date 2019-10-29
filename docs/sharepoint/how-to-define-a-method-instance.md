---
title: Как определить экземпляр метода | Документация Майкрософт
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
ms.openlocfilehash: 0e21900e87278ad500ee8497d1dd0c49350695d1
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981800"
---
# <a name="how-to-define-a-method-instance"></a>Как определить экземпляр метода
  Необходимо определить по крайней мере один экземпляр метода для каждого метода в модели.

 Добавьте экземпляр метода с помощью окна **сведения о методе BDC** . При добавлении экземпляра метода Visual Studio добавляет элемент `<MethodInstance>` в XML-код файла модели в проекте. Дополнительные сведения об атрибутах элемента `<MethodInstance>` см. в разделе [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

### <a name="to-define-a-method-instance"></a>Определение экземпляра метода

1. В окне **сведения о методе BDC** разверните узел метода, а затем узел **экземпляры** .

2. В списке **Добавить экземпляр метода** выберите **создать экземпляр Finder**.

     Новый экземпляр метода отображается под узлом **экземпляры** .

3. В строке меню выберите **вид** > **Свойства окно**.

4. В окне **Свойства** задайте свойства экземпляра метода. Дополнительные сведения о каждом свойстве см. в разделе [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

## <a name="see-also"></a>См. также
- [Обзор средств проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Как добавить сущность в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Как добавить параметр в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Как определить дескриптор типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
