---
title: Инициализировать диалоговое окно «взаимосвязь» | Документы Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aac62d4439c2280e977ef929c79bb103348c170a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="initialize-correlation-dialog-box"></a>Диалоговое окно «Инициализация корреляции»

**Инициализация корреляции** использовании диалоговое окно для редактирования в конструкторе рабочих процессов Windows <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> свойство <xref:System.ServiceModel.Activities.InitializeCorrelation> действия. Дополнительные сведения см. в разделе [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) раздела.

 В следующей таблице описаны элементы пользовательского интерфейса (UI) **инициализация корреляции** диалоговое окно.

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**Корреляция**|Дескриптор корреляции <xref:System.ServiceModel.Activities.CorrelationHandle> для инициализации.|
|**Инициализация**|По ключу/паре значений, содержащих данные инициализации. Это соответствует свойству <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Примером пару допустимый ключ значение будет раздел с именем «OrderID», связанное с переменной с именем OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Вызов диалогового окна «Инициализация корреляции»

-   Нажмите кнопку **представление** на **InitializeCorrelation** действия конструктора или выберите <xref:System.ServiceModel.Activities.InitializeCorrelation> действия в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] и затем нажмите кнопку с многоточием рядом с <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> свойства в сетки свойств.

## <a name="see-also"></a>См. также

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)