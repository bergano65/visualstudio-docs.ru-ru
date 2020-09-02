---
title: Диалоговое окно "определение CorrelatesOn" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2a9a6f7ec6b8bf246ebfc03c166780b229e1aee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656941"
---
# <a name="correlateson-definition-dialog-box"></a>Диалоговое окно «Корреляция по определению»
Диалоговое окно **CorrelatesOn** используется в [!INCLUDE[wfd1](../includes/wfd1-md.md)] для изменения <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> свойства <xref:System.ServiceModel.Activities.Receive> действия. [!INCLUDE[crdefault](../includes/crdefault-md.md)] раздел [Receive](../workflow-designer/receive-activity-designer.md) .

 Корреляция между действиями <xref:System.ServiceModel.Activities.Receive> указывает, как разные операции службы соединяются друг с другом в рабочем процессе.

 В следующей таблице описаны элементы ПОЛЬЗОВАТЕЛЬСКОГО интерфейса диалогового окна **CorrelatesOn** .

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**CorrelatesWith**|Метод <xref:System.ServiceModel.Activities.CorrelationHandle>, используемый для перенаправления сообщения в соответствующий экземпляр рабочего процесса.|
|**Запросы XPath**|Пара «ключ/значение», содержащая запросы, использованные для извлечения данных корреляции из входящих сообщений. Это соответствует свойству <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Запросы XPath содержатся в объекте <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Запуск диалогового окна «CorrelatesOn»
 Конструктор операций **получения** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия. При этом создается действие <xref:System.ServiceModel.Activities.Receive> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для Receive. Выберите конструктор действий **получения** и нажмите кнопку с многоточием рядом с текстом (коллекция) для свойства **CorrelatesOn** в сетке свойств в диалоговом окне **Определение CorrelatesOn** .

## <a name="see-also"></a>См. также:
 <xref:System.ServiceModel.Activities.Receive>Диалоговое окно ["Добавление CorrelationInitializers" диалогового окна "](../workflow-designer/add-correlationinitializers-dialog-box.md) [Инициализация корреляции](../workflow-designer/initialize-correlation-dialog-box.md) "