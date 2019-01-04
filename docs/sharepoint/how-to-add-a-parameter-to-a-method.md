---
title: Как выполнить Добавление параметра в метод | Документация Майкрософт
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f7d0e0ab164bf30c341ca093908be3661452d19
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866261"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Как выполнить Добавление параметра в метод
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
  
8.  Измените дескриптор типа параметра. Дополнительные сведения см. в разделе [Как Определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>См. также
 [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Практическое руководство. Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Практическое руководство. Определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Практическое руководство. Определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)   
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)  
