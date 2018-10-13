---
title: 'Как: вызов операции контракта Windows Communication Foundation (для прежних версий) | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 5e59d5ed9617d4be71a0542e35dd509d9035ae33
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181848"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Как вызвать операцию контракта Windows Communication Foundation (для прежних версий)
В данном разделе описывается вызов операции контракта [!INCLUDE[indigo1](../includes/indigo1-md.md)] с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 После перетаскивания **SendActivity** действия из области элементов в область конструктора рабочих процессов, необходимо импортировать существующий контракт и определить, какая операция будет вызываться из **SendActivity** действие. Выбор контракта и операции с его помощью [выберите операцию диалоговое окно (для прежних версий)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Также, если используется файл конфигурации для службы, необходимо указать объект класса <xref:System.Workflow.Activities.ChannelToken>. Объект класса <xref:System.Workflow.Activities.ChannelToken> определяет конфигурацию конечной точки действия отправки, которую оно предполагает использовать для подключения к службе рабочего процесса.  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Вызов операции контракта WCF из действия SendActivity  
  
1.  Дважды щелкните **SendActivity** действия в конструкторе или нажмите кнопку с многоточием рядом **ServiceOperationInfo** свойство в **свойства** области.  
  
2.  Когда **выбрать операцию** откроется диалоговое окно, нажмите кнопку **импорта** в правом верхнем углу диалогового окна.  
  
     [Обзор и Выбор типа .NET диалоговое окно (для прежних версий)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) открывает.  
  
3.  Найдите сборку или проект, который содержит нужный контракт.  
  
4.  Выберите контракт и нажмите кнопку **ОК**.  
  
5.  В разделе **доступные операции**, выберите операцию, необходимо вызвать и нажмите кнопку **ОК**.  
  
### <a name="to-specify-a-channel-token"></a>Определение маркера канала  
  
1.  Выделите действие <xref:System.Workflow.Activities.SendActivity> в конструкторе.  
  
2.  В **свойства** области, укажите имя для <xref:System.Workflow.Activities.ChannelToken>. Имя однозначно идентифицирует маркер канала.  
  
3.  Раскройте узел маркера канала и введите имя для клиентской конечной точки в поле <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>, которую предполагается использовать. Для конфигурации канала будет использоваться конфигурация конечной точки с тем же именем в файле конфигурации.  
  
4.  Создайте конфигурацию конечной точки в файле конфигурации, если она в нем не существует. Дополнительные сведения о настройке клиента см. в разделе [WCF Client Overview](http://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).  
  
## <a name="see-also"></a>См. также  
 [Выберите диалоговое окно «операции» (для прежних версий)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Практическое: реализовать операцию контракта WCF (для прежних версий)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)