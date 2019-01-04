---
title: Конструктор рабочих процессов - диалоговое окно инициализации корреляции
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51f001e053b0c2fdfe892175b00ed3f39dc6f1b4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829765"
---
# <a name="initialize-correlation-dialog-box"></a>Диалоговое окно «Инициализация корреляции»

**Инициализация корреляции** диалоговое окно используется в конструкторе рабочих процессов для изменения <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> свойство <xref:System.ServiceModel.Activities.InitializeCorrelation> действия. Дополнительные сведения см. в разделе [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

В следующей таблице описаны элементы пользовательского интерфейса (UI) **инициализация корреляции** диалоговое окно:

|Элемент пользовательского интерфейса|Описание|
|-|-----------------|
|**Корреляция**|Дескриптор корреляции <xref:System.ServiceModel.Activities.CorrelationHandle> для инициализации.|
|**Инициализировать на**|По ключу/паре значений, содержащих данные инициализации. Это значение соответствует <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> свойство. Например пары "допустимый ключ значение", раздел с именем «OrderID» связан с переменной с именем OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Вызов диалогового окна «Инициализация корреляции»

Нажмите кнопку **представление** на **InitializeCorrelation** действие конструктора или выберите <xref:System.ServiceModel.Activities.InitializeCorrelation> действия в конструкторе рабочих процессов. Щелкните кнопку с многоточием рядом с полем <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> свойства в сетке свойств.

## <a name="see-also"></a>См. также

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)