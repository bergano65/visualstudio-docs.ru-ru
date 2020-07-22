---
title: Диалоговое окно «Определение конструктор рабочих процессов-CorrelatesOn»
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d2db5bbfa4f34d86d3bf20cfe6bcc42b3dc00d0
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876129"
---
# <a name="correlateson-definition-dialog-box"></a>Диалоговое окно «Корреляция по определению»

Диалоговое окно **CorrelatesOn** используется в конструктор рабочих процессов для изменения <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> свойства <xref:System.ServiceModel.Activities.Receive> действия. Дополнительные сведения см. в разделе [конструктор действий Receive](../workflow-designer/receive-activity-designer.md).

Корреляция между действиями <xref:System.ServiceModel.Activities.Receive> указывает, как разные операции службы соединяются друг с другом в рабочем процессе.

В следующей таблице описаны элементы ПОЛЬЗОВАТЕЛЬСКОГО интерфейса диалогового окна **CorrelatesOn** .

|Элемент пользовательского интерфейса|Описание|
|-|-----------------|
|**CorrelatesWith**|Метод <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для перенаправления сообщения в соответствующий экземпляр рабочего процесса.|
|**Запросы XPath**|Пара «ключ/значение», содержащая запросы, использованные для извлечения данных корреляции из входящих сообщений. Это значение соответствует <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> свойству. Запросы XPath содержатся в объекте <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Запуск диалогового окна «CorrelatesOn»

Конструктор операций **получения** можно перетащить из **панели элементов** в конструктор рабочих процессов поверхность, где обычно размещаются действия. При удалении конструктора действий создается <xref:System.ServiceModel.Activities.Receive> действие со значением Receive, заданным по умолчанию <xref:System.Activities.Activity.DisplayName%2A> . Чтобы открыть диалоговое окно **Определение CorrelatesOn** , выберите Конструктор действий **получения** , а затем в сетке свойств нажмите кнопку с многоточием рядом с текстом коллекции для свойства **CorrelatesOn** .

## <a name="see-also"></a>См. также раздел

- <xref:System.ServiceModel.Activities.Receive>
- [Диалоговое окно "Добавление инициализаторов корреляции"](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Диалоговое окно "Инициализация корреляции"](../workflow-designer/initialize-correlation-dialog-box.md)