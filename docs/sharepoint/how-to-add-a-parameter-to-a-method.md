---
title: 'Практическое: Добавление параметра в метод | Документация Майкрософт'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 196ac37cc9bc4f53cfa886b92c62c7a301c3451a
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756315"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Практическое: Добавление параметра в метод
  Параметр для передачи информации в методе или для возвращения сведений из метода. Все методы должны иметь по крайней мере один параметр. Дополнительные сведения о создании параметра, поддерживающего тип метода, который вы хотите создать, см. в разделе [проектирование Business Data Connectivity Model](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 При добавлении параметра в метод, Visual Studio добавляет элемент параметра к XML-файла модели в проекте. Дополнительные сведения об атрибутах элемент параметра см. в разделе [параметр](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>Добавление параметра в метод  
  
1.  Добавьте метод в сущность.  
  
2.  В строке меню выберите **представление** > **Other Windows** > **Подробности метода BDC**.  
  
     **Подробности метода BDC** откроется окно. Дополнительные сведения см. в разделе [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  В **Подробности метода BDC** окне разверните узел метода и раскройте **параметры** узла.  
  
4.  В **добавьте параметр** выберите **создать параметр**.  
  
     Новый параметр появится под **параметры** узла.  
  
5.  В строке меню выберите **представление** > **окно "Свойства"**.  
  
6.  В **свойства** окне **имя** присвоено любое имя, которое имеет смысл. Например, если метод должен возвращать клиентов, можно назвать метод **GetCustomers**.  
  
7.  В **Подробности метода BDC** окно, откройте список, который отображается для направления параметра и выберите пункт **в**, **InOut**, **Out**, или **возвращают**.  
  
     Дополнительные сведения о направление, в котором для выбора для типа метода, который вы создаете, см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Измените дескриптор типа параметра. Дополнительные сведения см. в разделе [как: определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>См. также
 [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Практическое: Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Практическое: определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Практическое: определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)   
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
