---
title: 'Как: Добавление параметра в метод | Документы Microsoft'
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
ms.openlocfilehash: 9268fd0deb463a29c8e6d19e98ad63c86b965292
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767092"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>Как: Добавление параметра в метод
  Параметр для передачи сведений в метод или возвращения сведений из метода. Все методы должны иметь по крайней мере один параметр. Дополнительные сведения о создании параметра, поддерживающего тип метода, который вы хотите создать см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 При добавлении параметра в метод Visual Studio добавляет элемент параметра к XML-файла модели в проекте. Дополнительные сведения об атрибутах элемент параметра см. в разделе [параметр](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### <a name="to-add-a-parameter-to-a-method"></a>Добавление параметра в метод  
  
1.  Добавьте метод в сущность.  
  
2.  В строке меню выберите **представление** > **другие окна** > **Подробности метода BDC**.  
  
     **Подробности метода BDC** открывается окно. Дополнительные сведения см. в разделе [Обзор средств проектирования модели BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  В **Подробности метода BDC** разверните узел метода и затем разверните **параметры** узла.  
  
4.  В **добавьте параметр** выберите **создать параметр**.  
  
     Новый параметр отображается под **параметры** узла.  
  
5.  В строке меню выберите **представление** > **окно свойств**.  
  
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
  
