---
title: "Как: Добавление параметра в метод | Документы Microsoft"
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
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 388ce91d8500cf21c4a4989b8db9106a4d19693d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Практическое руководство. Добавление параметра в метод
  Параметр для передачи сведений в метод или возвращения сведений из метода. Все методы должны иметь по крайней мере один параметр. Дополнительные сведения о создании параметра, поддерживающего тип метода, который вы хотите создать см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 При добавлении параметра в метод Visual Studio добавляет `<Parameter>` элемент в XML файла модели в проекте. Дополнительные сведения об атрибутах `<Parameter>` элемент, в разделе [параметр](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>Добавление параметра в метод  
  
1.  Добавьте метод в сущность.  
  
2.  В строке меню выберите **представление**, **другие окна**, **Подробности метода BDC**.  
  
     **Подробности метода BDC** открывается окно. Дополнительные сведения см. в разделе [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  В **Подробности метода BDC** разверните узел метода и затем разверните **параметры** узла.  
  
4.  В **добавьте параметр** выберите **создать параметр**.  
  
     Новый параметр отображается под **параметры** узла.  
  
5.  В строке меню выберите **представление**, **окно свойств**.  
  
6.  В **свойства** задайте **имя** свойства любое имя, которое имеет смысл. Например, если метод должен возвращать клиентов, вы назовите метод **GetCustomers**.  
  
7.  В **Подробности метода BDC** откройте список, отображаемый для направления параметра и нажмите кнопку **в**, **InOut**, **Out**, или **возвращают**.  
  
     Дополнительные сведения о том, чтобы выбрать для создаваемого метода типа, для которого создается направление см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Измените дескриптор типа параметра. Дополнительные сведения см. в разделе [как: определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>См. также  
 [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Как: Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Как: определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Как: определение экземпляра метода](../sharepoint/how-to-define-a-method-instance.md)   
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  