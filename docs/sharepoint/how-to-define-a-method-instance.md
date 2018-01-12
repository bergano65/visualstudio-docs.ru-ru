---
title: "Как: определение экземпляра метода | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: aa5f1adcaacacd2b9e08d4c12cdcafbd5f561200
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-define-a-method-instance"></a>Практическое руководство. Определение экземпляра метода
  Необходимо определить хотя бы один экземпляр метода для каждого метода в модели.  
  
 Добавление экземпляра метода с помощью **Подробности метода BDC** окна. При добавлении экземпляра метода Visual Studio добавляет `<MethodInstance>` элемент в XML файла модели в проекте. Дополнительные сведения об атрибутах `<MethodInstance>` элемент, в разделе [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### <a name="to-define-a-method-instance"></a>Определение экземпляра метода  
  
1.  В **Подробности метода BDC** окна, разверните узел метода и разверните **экземпляров** узла.  
  
2.  В **Добавление экземпляра метода** выберите **создать экземпляр метода поиска**.  
  
     Новый экземпляр метода появится под **экземпляров** узла.  
  
3.  В строке меню выберите **представление**, выберите **окно свойств**.  
  
4.  В **свойства** задайте свойства экземпляра метода. Дополнительные сведения о каждом свойстве см. в разделе [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## <a name="see-also"></a>См. также  
 [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Как: Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Как: Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Как: определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  