---
title: Диалоговое окно «Инициализация корреляции» | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ab913027a6a992494dad609b98ab11dbc6ae61c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659041"
---
# <a name="initialize-correlation-dialog-box"></a>Диалоговое окно «Инициализация корреляции»
Диалоговое окно « **Инициализация корреляции** » используется в [!INCLUDE[wfd1](../includes/wfd1-md.md)] для изменения свойства <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> действия <xref:System.ServiceModel.Activities.InitializeCorrelation>. [!INCLUDE[crdefault](../includes/crdefault-md.md)] разделе [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) .

 В следующей таблице описаны элементы ПОЛЬЗОВАТЕЛЬСКОГО интерфейса диалогового окна « **Инициализация корреляции** ».

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**Корреляция**|Дескриптор корреляции <xref:System.ServiceModel.Activities.CorrelationHandle> для инициализации.|
|**Инициализировать в**|По ключу/паре значений, содержащих данные инициализации. Это соответствует свойству <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Пример допустимого ключа/пары значений: ключ с названием «OrderID», спаренный со значением, имя которого - «OrderID».|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Вызов диалогового окна «Инициализация корреляции»

- Нажмите кнопку **Просмотр** в конструкторе действий **InitializeCorrelation** или выберите <xref:System.ServiceModel.Activities.InitializeCorrelation> действие в [!INCLUDE[wfd2](../includes/wfd2-md.md)] а затем нажмите кнопку с многоточием рядом со свойством <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> в сетке свойств.

## <a name="see-also"></a>См. также раздел
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)