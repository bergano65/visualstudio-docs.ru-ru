---
title: Конструктор рабочих процессов - диалоговое окно «Определение CorrelatesOn»
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cba12e3e991282dc69ea5747d62db8761d6f8d16
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942639"
---
# <a name="correlateson-definition-dialog-box"></a>Диалоговое окно «Корреляция по определению»

**CorrelatesOn** диалоговое окно используется в конструкторе рабочих процессов для изменения <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> свойство <xref:System.ServiceModel.Activities.Receive> действия. Дополнительные сведения см. в разделе [получать конструктора действий](../workflow-designer/receive-activity-designer.md).

Корреляция между действиями <xref:System.ServiceModel.Activities.Receive> указывает, как разные операции службы соединяются друг с другом в рабочем процессе.

В следующей таблице описаны элементы пользовательского интерфейса (UI) **CorrelatesOn** диалоговое окно.

|Элемент пользовательского интерфейса|Описание:|
|-|-----------------|
|**CorrelatesWith**|Метод <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для перенаправления сообщения в соответствующий экземпляр рабочего процесса.|
|**Запросы XPath**|Пара «ключ/значение», содержащая запросы, использованные для извлечения данных корреляции из входящих сообщений. Это значение соответствует <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> свойство. Запросы XPath содержатся в объекте <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Запуск диалогового окна «CorrelatesOn»

**Receive** конструктор действия можно перетащить из **элементов** и сбрасываться в область конструктора рабочих процессов, везде, где обычно размещаются действия. Удаление конструктора действий создает <xref:System.ServiceModel.Activities.Receive> действие по умолчанию <xref:System.Activities.Activity.DisplayName%2A> функций получения. Чтобы открыть **корреляция по определению** выберите **Receive** действия конструктора, а затем в сетке свойств, выберите кнопку с многоточием рядом с текстом коллекции для  **Корреляция по** свойство.

## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Activities.Receive>
- [Диалоговое окно "Добавление инициализаторов корреляции"](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Добавление диалогового окна корреляции](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Диалоговое окно "Инициализация корреляции"](../workflow-designer/initialize-correlation-dialog-box.md)