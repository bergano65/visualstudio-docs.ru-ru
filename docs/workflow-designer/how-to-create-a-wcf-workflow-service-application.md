---
title: "Как: Создание приложения службы рабочего процесса WCF | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: "14"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 62eeab72ab88094f7986bb29bd6f3a55ad6aeff6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Как создать приложение службы рабочего процесса WCF
[!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] служебные приложения рабочего потока представляют собой распределенные службы коммуникаций, которые передают сообщения клиентам и обратно, из одного процесса в другой. В [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] реализация контракта службы на стороне службы выполняется декларативно с помощью действий рабочего процесса способом, аналогичным тому, который реализован в службах рабочих процессов .NET Framework 3.5.  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>Создание сервисного приложения рабочего процесса WCF  
  
1.  Запустите [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  На **файл** последовательно выберите пункты **New**, а затем выберите **проекта...** .  
  
     Откроется диалоговое окно **Новый проект** .  
  
3.  В **установленные шаблоны** выберите **WCF** или **рабочего процесса** либо из **Visual C#** или **Visual Basic** группирований, в зависимости от выбранного языка программирования.  
  
4.  В средней области выберите **приложение службы рабочего процесса WCF**.  
  
5.  В **имя** введите описательное имя проекта облегчить его определение.  
  
6.  В **расположение** введите каталог, в котором требуется сохранить проект, или **Обзор** для перехода к нему.  
  
7.  В **решения** выберите Создание нового решения и нажмите кнопку **ОК**.  
  
    > [!NOTE]
    >  Если вы хотите добавить консольное приложение рабочего процесса в существующее решение, откройте это решение в [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], щелкните правой кнопкой мыши решение в **обозревателе решений**и выберите **добавить**, затем  **Создать проект...**  Открытие **новый проект** диалоговое окно. Продолжайте действия, описанные ранее в этой процедуре.  
  
8.  Шаблон проекта создает определение службы как XAML. [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] открывает режим конструктора с действием <xref:System.Activities.Statements.Sequence>, которое содержит набор действий <xref:System.ServiceModel.Activities.Receive> и <xref:System.ServiceModel.Activities.SendReply>.  
  
## <a name="see-also"></a>См. также  
 [Как: Создание действия](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)   
 [Создание проекта рабочего процесса](../workflow-designer/creating-a-workflow-project.md)