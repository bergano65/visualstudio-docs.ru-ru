---
title: Как добавить параметр в метод | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb1a1c1e8f11ac6daa46f9fe1468a1ff3509e135
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986239"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Как добавить параметр в метод
  Используйте параметр для передачи сведений в метод или для возврата сведений из метода. Все методы должны иметь по крайней мере один параметр. Дополнительные сведения о проектировании параметра для поддержки типа создаваемого метода см. в разделе [Разработка модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

 При добавлении параметра в метод Visual Studio добавляет элемент Parameter в XML-файл модели в проекте. Дополнительные сведения об атрибутах элемента Parameter см. в разделе [параметр](/previous-versions/office/developer/sharepoint-2010/ee557705(v=office.14)).

### <a name="to-add-a-parameter-to-a-method"></a>Добавление параметра в метод

1. Добавьте метод в сущность.

2. В строке меню выберите **просмотреть** > другие > **сведения о методе BDC**в **Windows** .

     Откроется окно **сведения о методе BDC** . Дополнительные сведения см. в статье [Обзор средств проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. В окне **сведения о методе BDC** разверните узел метода, а затем разверните узел **Параметры** .

4. В списке **Добавить параметр** выберите **создать параметр**.

     Новый параметр отображается под узлом **Параметры** .

5. В строке меню выберите **вид** > **Свойства окно**.

6. В окне **Свойства** задайте для свойства **имя** любое имя, которое имеет смысл. Например, если метод вернет клиентов, можно присвоить методу имя **Customers**.

7. В окне **сведения о методе BDC** откройте список, который отображается для направления параметра, а затем выберите **in**, **InOut**, **out**или **return**.

     Дополнительные сведения о том, какое направление выбрать для создаваемого метода типа, см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

8. Измените дескриптор типа параметра. Дополнительные сведения см. [в разделе инструкции. определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>См. также
- [Обзор средств проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Как добавить сущность в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Как определить дескриптор типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Как определить экземпляр метода](../sharepoint/how-to-define-a-method-instance.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
