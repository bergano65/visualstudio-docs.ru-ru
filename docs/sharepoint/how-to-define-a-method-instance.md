---
title: Как выполнить Определение экземпляра метода | Документация Майкрософт
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 84a03fe6066911b12ba0e5a413ea3521033bc283
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952567"
---
# <a name="how-to-define-a-method-instance"></a>Как выполнить Определение экземпляра метода
  Необходимо определить хотя бы один экземпляр метода для каждого метода в модели.  
  
 Добавление экземпляра метода с помощью **Подробности метода BDC** окна. При добавлении экземпляра метода, Visual Studio добавляет `<MethodInstance>` элемент к XML-файла модели в проекте. Дополнительные сведения об атрибутах `<MethodInstance>` элемент, см. в разделе [экземпляр метода](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### <a name="to-define-a-method-instance"></a>Определение экземпляра метода  
  
1.  В **Подробности метода BDC** окне разверните узел метода и раскройте **экземпляров** узла.  
  
2.  В **Добавление экземпляра метода** выберите **создать экземпляр метода поиска**.  
  
     Новый экземпляр метода появится под **экземпляров** узла.  
  
3.  В строке меню выберите **представление** > **окно "Свойства"**.  
  
4.  В **свойства** окна, задайте свойства экземпляра метода. Дополнительные сведения о каждом свойстве см. в разделе [экземпляр метода](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## <a name="see-also"></a>См. также
 [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Практическое руководство. Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Практическое руководство. Определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)  
