---
title: Диалоговое окно «Определение CorrelatesOn» | Документы Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 930f291f68e62e70c4d2a03f490f84fd8d36f657
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="correlateson-definition-dialog-box"></a>Диалоговое окно «Корреляция по определению»
**CorrelatesOn** использовании диалоговое окно для редактирования в конструкторе рабочих процессов Windows <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> свойство <xref:System.ServiceModel.Activities.Receive> действия. Дополнительные сведения см. в разделе [Receive](../workflow-designer/receive-activity-designer.md) раздела.

 Корреляция между действиями <xref:System.ServiceModel.Activities.Receive> указывает, как разные операции службы соединяются друг с другом в рабочем процессе.

 В следующей таблице описаны элементы пользовательского интерфейса (UI) **CorrelatesOn** диалоговое окно.

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**CorrelatesWith**|Метод <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для перенаправления сообщения в соответствующий экземпляр рабочего процесса.|
|**Запросы XPath**|Пара «ключ/значение», содержащая запросы, использованные для извлечения данных корреляции из входящих сообщений. Это соответствует свойству <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Запросы XPath содержатся в объекте <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Запуск диалогового окна «CorrelatesOn»
 **Receive** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] , где обычно размещаются действия. При этом создается действие <xref:System.ServiceModel.Activities.Receive> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Receive. Выберите **Receive** конструктора действий и нажмите кнопку с многоточием рядом с текстом (коллекция) для **CorrelatesOn** свойства в сетке свойств для **корреляция по определению**  диалоговое окно.

## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Activities.Receive>
- [Диалоговое окно "Добавление инициализаторов корреляции"](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Добавить диалоговое окно «взаимосвязь»](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Диалоговое окно "Инициализация корреляции"](../workflow-designer/initialize-correlation-dialog-box.md)