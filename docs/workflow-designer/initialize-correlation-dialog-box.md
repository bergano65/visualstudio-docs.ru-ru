---
title: Конструктор рабочих процессов-диалоговое окно "Инициализация корреляции"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04f0a3bb70dbab31e0faa5c38caac9b54c6154fe
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114774"
---
# <a name="initialize-correlation-dialog-box"></a>Диалоговое окно «Инициализация корреляции»

Диалоговое окно « **Инициализация корреляции** » используется в конструктор рабочих процессов для изменения свойства <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> действия <xref:System.ServiceModel.Activities.InitializeCorrelation>. Дополнительные сведения см. в разделе [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

В следующей таблице описаны элементы ПОЛЬЗОВАТЕЛЬСКОГО интерфейса диалогового окна « **Инициализация корреляции** ».

|Элемент интерфейса|Описание|
|-|-----------------|
|**Корреляция**|Дескриптор корреляции <xref:System.ServiceModel.Activities.CorrelationHandle> для инициализации.|
|**Инициализировать в**|По ключу/паре значений, содержащих данные инициализации. Это значение соответствует свойству <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Примером допустимой пары "ключ-значение" является ключ с именем OrderID, состоящий из переменной с именем OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Вызов диалогового окна «Инициализация корреляции»

Нажмите кнопку **Просмотр** в конструкторе действий **InitializeCorrelation** или выберите <xref:System.ServiceModel.Activities.InitializeCorrelation> действие в конструктор рабочих процессов. Затем нажмите кнопку с многоточием рядом со свойством <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> в сетке свойств.

## <a name="see-also"></a>См. также:

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
