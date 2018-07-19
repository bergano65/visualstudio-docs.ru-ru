---
title: 'Практическое: определение экземпляра метода | Документация Майкрософт'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6e6dd6c0d7676c6b3c2071f0fcb07e8073313633
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119364"
---
# <a name="how-to-define-a-method-instance"></a>Практическое: определение экземпляра метода
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
 [Практическое: Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Практическое: Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Практическое: определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
