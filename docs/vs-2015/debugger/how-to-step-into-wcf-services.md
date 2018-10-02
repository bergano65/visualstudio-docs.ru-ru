---
title: 'Практическое: пошаговая отладка служб WCF | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b779c8bc2e6da3975f1f70265482c706c9141375
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563576"
---
# <a name="how-to-step-into-wcf-services"></a>Практическое руководство. Пошаговая отладка служб WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: пошаговая отладка служб WCF](https://docs.microsoft.com/visualstudio/debugger/how-to-step-into-wcf-services).  
  
В [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] можно выполнить пошаговую отладку службы WFC. Если служба WFC находится в том же решении [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], что и клиент, можно задавать точки останова внутри службы WCF.  
  
 Для начала работы необходимо включить отладку в файле app.config или Web.config. Сведения о том, как включить отладку и ограничениях на пошаговую отладку в службах WCF, см. в разделе [ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Выполнение пошаговой отладки служб WFC  
  
1.  Создайте решение [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], которое содержит проекты клиента WFC и службы WFC.  
  
2.  В обозревателе решений щелкните правой кнопкой мыши проект клиента WFC и нажмите кнопку **Назначить запускаемым проектом**.  
  
3.  Включите отладку в файле app.config или web.config. Дополнительные сведения см. в разделе [ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Установите точку останова в то место в проекте клиента, в котором необходимо начать пошаговую отладку. Как правило, точка останова задается непосредственно перед вызовом службы WCF.  
  
5.  Проведите выполнение до точки останова, затем начните пошаговую отладку. Отладчик выполнит пошаговую отладку службы автоматически.  
  
## <a name="see-also"></a>См. также  
 [Отладка служб WCF](../debugger/debugging-wcf-services.md)   
 [Ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Практическое руководство. Отладка резидентной службы WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md)



