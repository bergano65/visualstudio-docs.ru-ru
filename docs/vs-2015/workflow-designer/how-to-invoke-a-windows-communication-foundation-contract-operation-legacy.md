---
title: Практическое руководство. Вызов операции контракта Windows Communication Foundation (для прежних версий) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d42c9698c6d3a247601909909c49fa92d2d29978
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056670"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Практическое руководство. Вызов операции контракта Windows Communication Foundation (для прежних версий)
В данном разделе описывается вызов операции контракта [!INCLUDE[indigo1](../includes/indigo1-md.md)] с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 После перетаскивания **SendActivity** действия из области элементов в область конструктора рабочих процессов, необходимо импортировать существующий контракт и определить, какая операция будет вызываться из **SendActivity** действие. Выбор контракта и операции с его помощью [выберите операцию диалоговое окно (для прежних версий)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Также, если используется файл конфигурации для службы, необходимо указать объект класса <xref:System.Workflow.Activities.ChannelToken>. Объект класса <xref:System.Workflow.Activities.ChannelToken> определяет конфигурацию конечной точки действия отправки, которую оно предполагает использовать для подключения к службе рабочего процесса.  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Вызов операции контракта WCF из действия SendActivity  
  
1. Дважды щелкните **SendActivity** действия в конструкторе или нажмите кнопку с многоточием рядом **ServiceOperationInfo** свойство в **свойства** области.  
  
2. Когда **выбрать операцию** откроется диалоговое окно, нажмите кнопку **импорта** в правом верхнем углу диалогового окна.  
  
     [Обзор и Выбор типа .NET диалоговое окно (для прежних версий)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) открывает.  
  
3. Найдите сборку или проект, который содержит нужный контракт.  
  
4. Выберите контракт и нажмите кнопку **ОК**.  
  
5. В разделе **доступные операции**, выберите операцию, необходимо вызвать и нажмите кнопку **ОК**.  
  
### <a name="to-specify-a-channel-token"></a>Определение маркера канала  
  
1. Выделите действие <xref:System.Workflow.Activities.SendActivity> в конструкторе.  
  
2. В **свойства** области, укажите имя для <xref:System.Workflow.Activities.ChannelToken>. Имя однозначно идентифицирует маркер канала.  
  
3. Разверните узел маркера канала и введите имя для клиентской конечной точки в поле <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>, которую предполагается использовать. Для конфигурации канала будет использоваться конфигурация конечной точки с тем же именем в файле конфигурации.  
  
4. Создайте конфигурацию конечной точки в файле конфигурации, если она в нем не существует. Дополнительные сведения о настройке клиента см. в разделе [WCF Client Overview](http://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).  
  
## <a name="see-also"></a>См. также  
 [Выберите диалоговое окно «операции» (для прежних версий)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Практическое руководство. Реализация операции контракта WCF (для прежних версий)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)