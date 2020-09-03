---
title: Как вызвать операцию Windows Communication Foundation контракта (устаревшая) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f42600a739561a27a6dd8f6caa237027bac4554
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603704"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Как вызвать операцию контракта Windows Communication Foundation (для прежних версий)
В данном разделе описывается вызов операции контракта [!INCLUDE[indigo1](../includes/indigo1-md.md)] с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 После перетаскивания действия **SendActivity** из области элементов в рабочую область конструктора рабочих процессов необходимо импортировать существующий контракт и определить, какая операция будет вызываться из этого действия **SendActivity** . Вы выбираете контракт и его операции в [диалоговом окне Выбор операции (прежние версии)](../workflow-designer/choose-operation-dialog-box-legacy.md).

 Также, если используется файл конфигурации для службы, необходимо указать объект класса <xref:System.Workflow.Activities.ChannelToken>. Объект класса <xref:System.Workflow.Activities.ChannelToken> определяет конфигурацию конечной точки действия отправки, которую оно предполагает использовать для подключения к службе рабочего процесса.

### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Вызов операции контракта WCF из действия SendActivity

1. Дважды щелкните действие **SendActivity** в конструкторе или нажмите кнопку с многоточием рядом со свойством **ServiceOperationInfo** на панели **свойств** .

2. Когда откроется диалоговое окно **Выбор операции** , щелкните **Импорт** в правом верхнем углу диалогового окна.

     Откроется [диалоговое окно "Обзор и выбор типа .NET" (устаревшая)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) .

3. Найдите сборку или проект, который содержит нужный контракт.

4. Выберите контракт и нажмите кнопку **ОК**.

5. В разделе **Доступные операции**выберите операцию, которую требуется вызвать, и нажмите кнопку **ОК**.

### <a name="to-specify-a-channel-token"></a>Определение маркера канала

1. Выделите действие <xref:System.Workflow.Activities.SendActivity> в конструкторе.

2. На панели **Свойства** укажите имя <xref:System.Workflow.Activities.ChannelToken> . Имя однозначно идентифицирует маркер канала.

3. Разверните узел маркера канала и введите имя для клиентской конечной точки в поле <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>, которую предполагается использовать. Для конфигурации канала будет использоваться конфигурация конечной точки с тем же именем в файле конфигурации.

4. Создайте конфигурацию конечной точки в файле конфигурации, если она в нем не существует. Дополнительные сведения о настройке клиента см. в разделе [Общие сведения о клиенте WCF](https://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).

## <a name="see-also"></a>См. также:
 [Диалоговое окно «Выбор операции» (устаревшая)](../workflow-designer/choose-operation-dialog-box-legacy.md) [руководство. Реализация операций контракта WCF (устаревших)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [устаревшие действия рабочего процесса](../workflow-designer/legacy-workflow-activities.md)