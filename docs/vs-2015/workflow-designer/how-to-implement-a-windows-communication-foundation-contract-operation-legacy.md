---
title: 'Практическое: реализовать операцию контракта Windows Communication Foundation (для прежних версий) | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f4277de8f97951847bf448636fec1b9c652f9359
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563100"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Как реализовать операцию контракта Windows Communication Foundation (для прежних версий)
В этом разделе описывается реализация операции контракта [!INCLUDE[indigo1](../includes/indigo1-md.md)] с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 После перетаскивания **ReceiveActivity** действия из области элементов в область конструктора рабочих процессов либо создается новый [!INCLUDE[indigo2](../includes/indigo2-md.md)] контракта или импортировать существующий контракт и реализуются операции. Выбор или создание контракта и операции с его помощью [выберите операцию диалоговое окно (для прежних версий)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### <a name="to-implement-a-wcf-contract-operation"></a>Реализация операции контракта WCF  
  
1.  Дважды щелкните **ReceiveActivity** действия в конструкторе или нажмите кнопку с многоточием рядом **ServiceOperationInfo** свойство в **свойства** области.  
  
2.  Выполните одно из следующих действий.  
  
    -   Нажмите кнопку **добавить контракт** в правом верхнем углу диалогового окна. Будет создан новый контракт [!INCLUDE[indigo2](../includes/indigo2-md.md)] и операция.  
  
         - или -  
  
    -   Нажмите кнопку **импорта** в правом верхнем углу диалогового окна. [Обзор и Выбор типа .NET диалоговое окно (для прежних версий)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) открывает. Найдите сборку или проект, который содержит нужный контракт. Выберите контракт и нажмите кнопку **ОК**.  
  
     После создания или импортирования контракта к нему можно добавить новые операции. Чтобы добавить новую операцию, выберите контракт и нажмите кнопку **добавить операцию** в правом верхнем углу диалогового окна. После завершения добавления операций перейдите к шагу 3.  
  
3.  Выберите операцию, необходимо связать с **ReceiveActivity** действия. Управлять определением операции можно с помощью изменения имени операции, параметров, свойств и параметров разрешения.  
  
     Чтобы изменить имя, введите новое имя в **имя операции** текстовое поле.  
  
     Нажмите кнопку **параметры** tab, чтобы получить доступ к параметрам операции. Можно изменить имя, тип, направление параметра, а также добавить или удалить параметры из операции.  
  
     Нажмите кнопку **свойства** tab, чтобы доступ к функциям exchange операции защиты сообщения уровня и поддерживаемые операции.  
  
     Нажмите кнопку **разрешения** tab, чтобы указать группы, которым разрешено реализовывать операцию.  
  
4.  Нажмите кнопку **ОК** и **ReceiveActivity** действие будет отображаться имя операции для операции, которое он реализует.  
  
5.  Поместите действия рабочего процесса, который вы собираетесь использовать для реализации операции в рамках **ReceiveActivity** действия.  
  
## <a name="see-also"></a>См. также  
 [Выберите диалоговое окно «операции» (для прежних версий)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Как: вызов операции контракта WCF (для прежних версий)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)