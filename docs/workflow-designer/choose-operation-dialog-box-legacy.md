---
title: "Диалоговое окно &#171;Выбор операции&#187; (для прежних версий) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Design.OperationPickerDialog.UI"
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Диалоговое окно &#171;Выбор операции&#187; (для прежних версий)
В данном разделе описывается использование диалогового окна **Выбор операции** в средстве [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] прежних версий.[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Диалоговое окно **Выбрать операцию** используется для выбора операции, связанной с действием <xref:System.Workflow.Activities.ReceiveActivity> или действием <xref:System.Workflow.Activities.SendActivity>.Дополнительные сведения об использовании этого диалогового окна с этими действиями см. в разделах [Как реализовать операцию контракта WCF \(для прежних версий\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) и [Как вызвать операцию контракта WCF \(для прежних версий\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).  
  
 В следующей таблице приведено описание элементов пользовательского интерфейса диалогового окна **Выбрать операцию**.  
  
|Элемент пользовательского интерфейса|Описание|  
|------------------------------------------|--------------|  
|**Добавить  контракт**|Создает новый контракт.В этом контракте можно задать новые операции.\(Применяется только с объектом класса <xref:System.Workflow.Activities.ReceiveActivity>.\)|  
|**Добавить  операцию**|Добавляет новые операции в новый контракт, созданный в диалоговом окне **Выбрать операцию**. **Note:**  Новые операции можно добавить только в контракты, которые созданы посредством диалогового окна **Выбрать операцию**. <br /><br /> \(Применяется только с объектом класса <xref:System.Workflow.Activities.ReceiveActivity>.\)|  
|**Импорт...**|Импорт ранее определенного контракта, позволяет выбрать операцию из этого контракта.|  
|**Имя  операции**|Имя выбранной в настоящее время операции.Текстовое поле доступно для изменения только если операция создана посредством диалогового окна **Выбрать операцию**.|  
|**Параметры**|Вкладка, содержащая определения параметров выбранной в настоящее время операции. **Note:**  Определения параметров можно изменить только если операция создана посредством диалогового окна **Выбрать операцию**.|  
|**Свойства**|Вкладка, содержащая параметры <xref:System.Net.Security.ProtectionLevel> для сообщений, отправляемых между клиентом и службой. **Note:**  Вкладка доступна только если операция создана посредством диалогового окна **Выбрать операцию**.|  
|**Разрешения**|Вкладка содержит свойства пользователей <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> и <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A>, которые разрешается вызывать этой операции.Например, если вызывать эту операцию разрешается только пользователям группы "Администраторы", то необходимо написать "Администраторы" в текстовом поле **Роль**.<br /><br /> Вкладка доступна для обеих операций, созданных посредством диалогового окна **Выбрать операцию** и импортированных посредством кнопки **Импорт**.|  
  
> [!NOTE]
>  Диалоговое окно **Выбрать операцию** показывает только контракты или операции, которые используются другими действиями <xref:System.Workflow.Activities.SendActivity> в рабочем процессе.Точно также диалоговое окно **Выбрать операцию** для действий <xref:System.Workflow.Activities.ReceiveActivity> показывает только контракты или операции, которые используются другими действиями **ReceiveActivity** в рабочем процессе.  
  
## См. также  
 [Как реализовать операцию контракта WCF \(для прежних версий\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Как вызвать операцию контракта WCF \(для прежних версий\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Справка по интерфейсу пользователя конструктора прежних версий для Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)