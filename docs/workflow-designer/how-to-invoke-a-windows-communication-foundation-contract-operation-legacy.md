---
title: "Как вызвать операцию контракта Windows Communication Foundation (для прежних версий) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Как вызвать операцию контракта Windows Communication Foundation (для прежних версий)
В данном разделе описывается вызов операции контракта [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] с помощью средства [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 После перетаскивания действия **SendActivity** из области элементов на рабочую область конструктора рабочих процессов, необходимо импортировать существующий контракт и определить операцию, которая будет вызываться из действия **SendActivity**.Выбор контракта и его операций осуществляется посредством диалогового окна [Диалоговое окно «Выбор операции» \(для прежних версий\)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Также, если используется файл конфигурации для службы, необходимо указать объект класса <xref:System.Workflow.Activities.ChannelToken>.Объект класса <xref:System.Workflow.Activities.ChannelToken> определяет конфигурацию конечной точки действия отправки, которую оно предполагает использовать для подключения к службе рабочего процесса.  
  
### Вызов операции контракта WCF из действия SendActivity  
  
1.  Дважды щелкните действие **SendActivity** в конструкторе или нажмите кнопку с многоточием рядом со свойством **ServiceOperationInfo** на панели **Свойство**.  
  
2.  После открытия диалогового окна **Выбрать операцию**, нажмите кнопку **Импорт** в правом верхнем углу диалогового окна.  
  
     Откроется диалоговое окно [Диалоговое окно «Обзор и выбор типа .NET» \(для прежних версий\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).  
  
3.  Найдите сборку или проект, который содержит нужный контракт.  
  
4.  Выберите контракт и нажмите кнопку **ОК**.  
  
5.  В области **Доступные операции** выберите операцию, которую необходимо вызвать и нажмите кнопку **ОК**.  
  
### Определение маркера канала  
  
1.  Выделите действие <xref:System.Workflow.Activities.SendActivity> в конструкторе.  
  
2.  На панели **Свойства** введите имя объекта класса <xref:System.Workflow.Activities.ChannelToken>.Имя однозначно идентифицирует маркер канала.  
  
3.  Раскройте узел маркера канала и введите имя для клиентской конечной точки в поле <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>, которую предполагается использовать.Для конфигурации канала будет использоваться конфигурация конечной точки с тем же именем в файле конфигурации.  
  
4.  Создайте конфигурацию конечной точки в файле конфигурации, если она в нем не существует.Дополнительные сведения о настройке клиента см. в разделе [Общие сведения о клиентах WCF](../Topic/WCF%20Client%20Overview.md).  
  
## См. также  
 [Диалоговое окно «Выбор операции» \(для прежних версий\)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Как реализовать операцию контракта WCF \(для прежних версий\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)