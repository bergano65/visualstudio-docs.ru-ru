---
title: Конструктор рабочих процессов - диалоговое окно инициализации корреляции
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93ce95c7a821d243af842170ba30ec82647933ab
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971794"
---
# <a name="initialize-correlation-dialog-box"></a>Диалоговое окно «Инициализация корреляции»

**Инициализация корреляции** использовании диалоговое окно для редактирования в конструкторе рабочих процессов Windows <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> свойство <xref:System.ServiceModel.Activities.InitializeCorrelation> действия. Дополнительные сведения см. в разделе [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) раздела.

 В следующей таблице описаны элементы пользовательского интерфейса (UI) **инициализация корреляции** диалоговое окно.

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**Корреляция**|Дескриптор корреляции <xref:System.ServiceModel.Activities.CorrelationHandle> для инициализации.|
|**Инициализация**|По ключу/паре значений, содержащих данные инициализации. Это соответствует свойству <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Примером пару допустимый ключ значение будет раздел с именем «OrderID», связанное с переменной с именем OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Вызов диалогового окна «Инициализация корреляции»

-   Нажмите кнопку **представление** на **InitializeCorrelation** действия конструктора или выберите <xref:System.ServiceModel.Activities.InitializeCorrelation> действия в конструкторе рабочих процессов и нажмите кнопку с многоточием, расположенную рядом с <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> свойства в Сетка свойств.

## <a name="see-also"></a>См. также

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)