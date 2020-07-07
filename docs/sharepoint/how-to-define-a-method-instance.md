---
title: Как определить экземпляр метода | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 170982a5d4abe33ca8cd705a979acc0737185a9c
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016837"
---
# <a name="how-to-define-a-method-instance"></a>Как определить экземпляр метода
  Необходимо определить по крайней мере один экземпляр метода для каждого метода в модели.

 Добавьте экземпляр метода с помощью окна **сведения о методе BDC** . При добавлении экземпляра метода Visual Studio добавляет `<MethodInstance>` элемент в XML-код файла модели в проекте. Дополнительные сведения об атрибутах `<MethodInstance>` элемента см. в разделе [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

### <a name="to-define-a-method-instance"></a>Определение экземпляра метода

1. В окне **сведения о методе BDC** разверните узел метода, а затем узел **экземпляры** .

2. В списке **Добавить экземпляр метода** выберите **создать экземпляр Finder**.

     Новый экземпляр метода отображается под узлом **экземпляры** .

3. В строке меню выберите **вид**  >  **окно свойств**.

4. В окне **Свойства** задайте свойства экземпляра метода. Дополнительные сведения о каждом свойстве см. в разделе [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

## <a name="see-also"></a>См. также раздел
- [Обзор средств проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Как добавить сущность в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Как добавить параметр в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Как определить дескриптор типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
