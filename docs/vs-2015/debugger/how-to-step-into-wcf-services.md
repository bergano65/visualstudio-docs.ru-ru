---
title: Практическое руководство. Пошаговое выполнение служб WCF | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 951d5f39fbf3929d094cc18de5fe108b46753b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176523"
---
# <a name="how-to-step-into-wcf-services"></a>Практическое руководство. пошаговую отладку служб WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] можно выполнить пошаговую отладку службы WFC. Если служба WFC находится в том же решении [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], что и клиент, можно задавать точки останова внутри службы WCF.  
  
 Для начала работы необходимо включить отладку в файле app.config или Web.config. Сведения о включении отладки и ограничениях на пошаговое выполнение в службах WCF см. в разделе [Ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Выполнение пошаговой отладки служб WFC  
  
1. Создайте решение [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], которое содержит проекты клиента WFC и службы WFC.  
  
2. В обозревателе решений щелкните правой кнопкой мыши проект клиента WFC и выберите **Назначить запускаемым проектом**.  
  
3. Включите отладку в файле app.config или web.config. Дополнительные сведения см. в разделе [Ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4. Установите точку останова в то место в проекте клиента, в котором необходимо начать пошаговую отладку. Как правило, точка останова задается непосредственно перед вызовом службы WCF.  
  
5. Проведите выполнение до точки останова, затем начните пошаговую отладку. Отладчик выполнит пошаговую отладку службы автоматически.  
  
## <a name="see-also"></a>См. также:  
 [Отладка служб WCF](../debugger/debugging-wcf-services.md)   
 [Ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Практическое руководство. Отладка резидентной службы WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
