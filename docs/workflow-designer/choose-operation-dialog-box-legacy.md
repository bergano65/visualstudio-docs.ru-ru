---
title: "Выберите диалоговое окно «операция» (для прежних версий) | Документы Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b2d26d97fd147ea39e8d074ea65f4a4121f9be71
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="choose-operation-dialog-box-legacy"></a>Диалоговое окно «Выбор операции» (для прежних версий)

В этом разделе описывается использование **выбрать операцию** диалоговое окно в конструкторе рабочих процессов прежних версий Windows. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 **Выбрать операцию** диалоговое окно используется для выбора операции, связанной с <xref:System.Workflow.Activities.ReceiveActivity> действия или <xref:System.Workflow.Activities.SendActivity> действия. Дополнительные сведения об использовании данным диалоговым окном с этими действиями см. в разделе [как: реализовать операцию контракта WCF (для прежних версий)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) и [как: вызвать операцию контракта WCF (для прежних версий)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).

 В следующей таблице описаны элементы пользовательского интерфейса (UI) **выбрать операцию** диалоговое окно.

|Элемент пользовательского интерфейса|Описание:|
|----------------|-----------------|
|**Добавление контракта**|Создает новый контракт. В этом контракте можно задать новые операции. (Применяется только с объектом класса <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**Операция добавления**|Добавляет новый контракт, который был создан в новые операции **выбрать операцию** диалоговое окно. **Примечание:** новые операции можно добавлять только в контракты, которые созданы посредством **выбрать операцию** диалоговое окно. <br /><br /> (Применяется только с объектом класса <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**Импорт...**|Импорт ранее определенного контракта, позволяет выбрать операцию из этого контракта.|
|**Имя операции**|Имя выбранной в настоящее время операции. Это поле доступно для изменения только в том случае, если вы создали операцию с использованием **выбрать операцию** диалоговое окно.|
|**Параметры**|Вкладка, содержащая определения параметров выбранной в настоящее время операции. **Примечание:** определения параметров можно изменить только в том случае, если вы создали операцию с использованием **выбрать операцию** диалоговое окно.|
|**Свойства**|Вкладка, содержащая параметры <xref:System.Net.Security.ProtectionLevel> для сообщений, отправляемых между клиентом и службой. **Примечание:** вкладка доступна только в том случае, если вы создали операцию с использованием **выбрать операцию** диалоговое окно.|
|**Разрешения**|Вкладка содержит свойства пользователей <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> и <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A>, которые разрешается вызывать этой операции. Например, если только пользователи из группы «Администраторы» могли вызывать эту операцию, то необходимо написать «Администраторы» **роли** текстовое поле.<br /><br /> Эта вкладка активна для обеих операций, созданные с помощью **ChooseOperation** диалоговое окно и операций, которые были импортированы через **импорта** кнопки.|

> [!NOTE]
> **Выбрать операцию** диалоговое окно показывает только контракты или операции, которые используются другими <xref:System.Workflow.Activities.SendActivity> действия в рабочем процессе. Аналогичным образом **выбрать операцию** диалоговое окно для <xref:System.Workflow.Activities.ReceiveActivity> действий показывает только контракты или операции, которые используются другими **ReceiveActivity** действия в рабочем процессе.

## <a name="see-also"></a>См. также

- [Как: реализовать операцию контракта WCF (для прежних версий)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [Как: вызвать операцию контракта WCF (для прежних версий)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)
- [Справка по интерфейсу пользователя конструктора прежних версий для Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)