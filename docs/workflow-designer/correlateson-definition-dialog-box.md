---
title: Диалоговое окно «Определение конструктор рабочих процессов-CorrelatesOn»
description: Узнайте, как можно использовать диалоговое окно CorrelatesOn в конструктор рабочих процессов для изменения свойства CorrelatesOn действия Receive.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2be38ba9521762c38c629c2817a7c8e8ca5a709a
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438130"
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