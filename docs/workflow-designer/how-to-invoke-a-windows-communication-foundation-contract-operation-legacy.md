---
title: 'Как: вызвать операцию контракта Windows Communication Foundation (для прежних версий) | Документы Microsoft'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c97b62f7ddfbe46ac5ede4aefba53e50020f3b65
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Как вызвать операцию контракта Windows Communication Foundation (для прежних версий)
В этом разделе описывается вызов [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] операции, используя конструктор рабочего процесса прежних версий Windows, предназначенного контракта [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 После перетаскивания **SendActivity** действия из области элементов в область конструктора рабочих процессов, необходимо импортировать существующий контракт и определить, какая операция будет вызываться из **SendActivity** действие. Выбор контракта и операции с его помощью [выберите операцию диалоговое окно (для прежних версий)](../workflow-designer/choose-operation-dialog-box-legacy.md).

 Также, если используется файл конфигурации для службы, необходимо указать объект класса <xref:System.Workflow.Activities.ChannelToken>. Объект класса <xref:System.Workflow.Activities.ChannelToken> определяет конфигурацию конечной точки действия отправки, которую оно предполагает использовать для подключения к службе рабочего процесса.

### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Вызов операции контракта WCF из действия SendActivity

1.  Дважды щелкните **SendActivity** действия в конструкторе или нажмите кнопку с многоточием рядом с **ServiceOperationInfo** свойство в **свойства** области.

2.  Когда **выбрать операцию** откроется диалоговое окно, нажмите кнопку **импорта** в правом верхнем углу диалогового окна.

     [Обзор и выбор диалоговое окно типа .NET (для прежних версий)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) открывается.

3.  Найдите сборку или проект, который содержит нужный контракт.

4.  Выберите контракт и нажмите кнопку **ОК**.

5.  В разделе **доступные операции**, выберите операцию, необходимо вызвать и нажмите кнопку **ОК**.

### <a name="to-specify-a-channel-token"></a>Определение маркера канала

1.  Выделите действие <xref:System.Workflow.Activities.SendActivity> в конструкторе.

2.  В **свойства** области, укажите имя для <xref:System.Workflow.Activities.ChannelToken>. Имя однозначно идентифицирует маркер канала.

3.  Раскройте узел маркера канала и введите имя для клиентской конечной точки в поле <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>, которую предполагается использовать. Для конфигурации канала будет использоваться конфигурация конечной точки с тем же именем в файле конфигурации.

4.  Создайте конфигурацию конечной точки в файле конфигурации, если она в нем не существует. Дополнительные сведения о настройке вашего клиента см. в разделе [Общие сведения о клиенте WCF](/dotnet/framework/wcf/wcf-client-overview).

## <a name="see-also"></a>См. также

- [Диалоговое окно "Выбор операции" (для прежних версий)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [Как: реализовать операцию контракта WCF (для прежних версий)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)