---
title: Как выполнить Пошаговая отладка служб WCF | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f361369aef97aaa894a1a1929149356d3177cc3f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890739"
---
# <a name="how-to-step-into-wcf-services"></a>Как выполнить пошаговую отладку служб WCF
В [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] можно выполнить пошаговую отладку службы WFC. Если служба WFC находится в том же решении [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], что и клиент, можно задавать точки останова внутри службы WCF.  
  
 Для начала работы необходимо включить отладку в файле app.config или Web.config. Сведения о том, как включить отладку и ограничениях на пошаговую отладку в службах WCF, см. в разделе [ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Выполнение пошаговой отладки служб WFC  
  
1. Создайте решение [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], которое содержит проекты клиента WFC и службы WFC.  
  
2. В обозревателе решений щелкните правой кнопкой мыши проект клиента WFC и выберите **Назначить запускаемым проектом**.  
  
3. Включите отладку в файле app.config или web.config. Дополнительные сведения см. в разделе [ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4. Установите точку останова в то место в проекте клиента, в котором необходимо начать пошаговую отладку. Как правило, точка останова задается непосредственно перед вызовом службы WCF.  
  
5. Проведите выполнение до точки останова, затем начните пошаговую отладку. Отладчик выполнит пошаговую отладку службы автоматически.  
  
## <a name="see-also"></a>См. также раздел  
 [Отладка служб WCF](../debugger/debugging-wcf-services.md)   
 [Ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Практическое руководство. Отладка резидентной службы WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md)