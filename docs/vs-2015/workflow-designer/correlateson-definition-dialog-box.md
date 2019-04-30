---
title: Диалоговое окно CorrelatesOn Definition | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fd03e1a8615e75d3f00f79eb10b7a7ff97f0eb33
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977376"
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
 [Диалоговое окно "Инициализация корреляции"](../workflow-designer/initialize-correlation-dialog-box.md)