---
title: Диалоговое окно «Выбор операции» (устаревшая) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2736db7e18733a9477238cafad21088eb135e89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659164"
---
# <a name="choose-operation-dialog-box-legacy"></a>Диалоговое окно «Выбор операции» (для прежних версий)
В этом разделе описывается использование диалогового окна **Выбор операции** в [!INCLUDE[wfd1](../includes/wfd1-md.md)] устаревших версий. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Диалоговое окно **Выбор операции** используется для выбора операции, связываемой с <xref:System.Workflow.Activities.ReceiveActivity> действием или <xref:System.Workflow.Activities.SendActivity> действием. Дополнительные сведения об использовании этого диалогового окна с этими действиями см. в статьях [как реализовать операцию контракта WCF (устаревшая)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) и [как вызвать операцию контракта WCF (устаревшая)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).

 В следующей таблице описаны элементы ПОЛЬЗОВАТЕЛЬСКОГО интерфейса диалогового окна « **Выбор операции** ».

|Элемент пользовательского интерфейса|Описание|
|----------------|-----------------|
|**Добавить контракт**|Создает новый контракт. В этом контракте можно задать новые операции. (Применяется только с объектом класса <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**Добавить операцию**|Добавляет новые операции в новый контракт, созданный в диалоговом окне **Выбор операции** . **Примечание.**  Новые операции можно добавлять только в контракты, созданные с помощью диалогового окна **Выбор операции** . <br /><br /> (Применяется только с объектом класса <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**Импорт...**|Импорт ранее определенного контракта, позволяет выбрать операцию из этого контракта.|
|**Имя операции**|Имя выбранной в настоящее время операции. Это текстовое поле доступно для редактирования только в том случае, если вы создали операцию с помощью диалогового окна **Выбор операции** .|
|**Параметры**|Вкладка, содержащая определения параметров выбранной в настоящее время операции. **Примечание.**  Определения параметров можно изменять только в том случае, если вы создали операцию с помощью диалогового окна **Выбор операции** .|
|**Свойства**|Вкладка, содержащая параметры <xref:System.Net.Security.ProtectionLevel> для сообщений, отправляемых между клиентом и службой. **Примечание.**  Эта вкладка доступна, только если вы создали операцию с помощью диалогового окна **Выбор операции** .|
|**Разрешения**|Вкладка содержит свойства пользователей <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> и <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A>, которые разрешается вызывать этой операции. Например, если только пользователям из группы "Администраторы" разрешено вызывать эту операцию, в текстовом поле **роль** будет записано «Администраторы».<br /><br /> Эта вкладка включена для обеих операций, созданных с помощью диалогового окна **чусеоператион** , и операций, импортированных с помощью кнопки **Импорт** .|

> [!NOTE]
> В диалоговом окне **Выбор операции** отображаются только контракты или операции, используемые другими действиями <xref:System.Workflow.Activities.SendActivity> в рабочем процессе. Аналогично, диалоговое окно **Выбор операции** для действий <xref:System.Workflow.Activities.ReceiveActivity> отображает только контракты или операции, используемые другими действиями **ReceiveActivity** в рабочем процессе.

## <a name="see-also"></a>См. также раздел
 [Как реализовать операцию контракта WCF (устаревшая)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [: как вызвать устаревший конструктор операций контракта WCF (устаревший)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [для справки по пользовательскому интерфейсу Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)