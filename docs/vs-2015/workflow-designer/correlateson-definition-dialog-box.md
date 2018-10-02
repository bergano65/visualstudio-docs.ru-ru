---
title: Диалоговое окно CorrelatesOn Definition | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 01af296f4cb7dcaa7785438c54527337c110f609
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560009"
---
# <a name="correlateson-definition-dialog-box"></a>Диалоговое окно «Корреляция по определению»
**CorrelatesOn** диалоговое окно используется в [!INCLUDE[wfd1](../includes/wfd1-md.md)] изменение <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> свойство <xref:System.ServiceModel.Activities.Receive> действия. [!INCLUDE[crdefault](../includes/crdefault-md.md)] [Receive](../workflow-designer/receive-activity-designer.md) раздела.  
  
 Корреляция между действиями <xref:System.ServiceModel.Activities.Receive> указывает, как разные операции службы соединяются друг с другом в рабочем процессе.  
  
 В следующей таблице описаны элементы пользовательского интерфейса (UI) **CorrelatesOn** диалоговое окно.  
  
|Элемент пользовательского интерфейса|Описание|  
|----------------|-----------------|  
|**CorrelatesWith**|Метод <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для перенаправления сообщения в соответствующий экземпляр рабочего процесса.|  
|**Запросы XPath**|Пара «ключ/значение», содержащая запросы, использованные для извлечения данных корреляции из входящих сообщений. Это соответствует свойству <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Запросы XPath содержатся в объекте <xref:System.ServiceModel.MessageQuerySet>.|  
  
## <a name="to-launch-the-correlateson-dialog-box"></a>Запуск диалогового окна «CorrelatesOn»  
 **Receive** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия. При этом создается действие <xref:System.ServiceModel.Activities.Receive> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Receive. Выберите **Receive** конструктора действий и нажмите кнопку с многоточием, расположенную рядом с текстом (коллекция) для **CorrelatesOn** свойства в сетке свойств для **корреляция по определению**  диалоговое окно.  
  
## <a name="see-also"></a>См. также  
 <xref:System.ServiceModel.Activities.Receive>   
 [Добавление инициализаторов корреляции диалогового окна](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [Добавление диалогового окна корреляции](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [Диалоговое окно "Инициализация корреляции"](../workflow-designer/initialize-correlation-dialog-box.md)