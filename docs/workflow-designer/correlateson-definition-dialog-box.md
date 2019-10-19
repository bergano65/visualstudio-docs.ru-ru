---
title: Диалоговое окно «Определение конструктор рабочих процессов-CorrelatesOn»
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 401f72f55f23779f7c6257437034a4ebc294d219
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650600"
---
# <a name="correlateson-definition-dialog-box"></a>Диалоговое окно «Корреляция по определению»

Диалоговое окно **CorrelatesOn** используется в конструктор рабочих процессов для изменения свойства <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> действия <xref:System.ServiceModel.Activities.Receive>. Дополнительные сведения см. в разделе [конструктор действий Receive](../workflow-designer/receive-activity-designer.md).

Корреляция между действиями <xref:System.ServiceModel.Activities.Receive> указывает, как разные операции службы соединяются друг с другом в рабочем процессе.

В следующей таблице описаны элементы ПОЛЬЗОВАТЕЛЬСКОГО интерфейса диалогового окна **CorrelatesOn** .

|Элемент пользовательского интерфейса|Описание|
|-|-----------------|
|**CorrelatesWith**|Метод <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для перенаправления сообщения в соответствующий экземпляр рабочего процесса.|
|**Запросы XPath**|Пара «ключ/значение», содержащая запросы, использованные для извлечения данных корреляции из входящих сообщений. Это значение соответствует свойству <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Запросы XPath содержатся в объекте <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Запуск диалогового окна «CorrelatesOn»

Конструктор операций **получения** можно перетащить из **панели элементов** в конструктор рабочих процессов поверхность, где обычно размещаются действия. При удалении конструктора действий создается действие <xref:System.ServiceModel.Activities.Receive> с <xref:System.Activities.Activity.DisplayName%2A>ом Receive по умолчанию. Чтобы открыть диалоговое окно **Определение CorrelatesOn** , выберите Конструктор действий **получения** , а затем в сетке свойств нажмите кнопку с многоточием рядом с текстом коллекции для свойства **CorrelatesOn** .

## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Activities.Receive>
- [Диалоговое окно "Добавление инициализаторов корреляции"](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Диалоговое окно "Инициализация корреляции"](../workflow-designer/initialize-correlation-dialog-box.md)