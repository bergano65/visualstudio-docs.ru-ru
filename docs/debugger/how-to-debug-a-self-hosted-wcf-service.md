---
title: Как выполнить Отладка резидентной службы WCF | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f19122407f3105d32ad9dfed182cc237a614f05c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030292"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Как выполнить отладку резидентной службы WCF
*Резидентная служба* является службой WCF, которая не запускается внутри IIS, узла службы WCF или сервера разработки [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Самый легкий путь отладки резидентной WCF — это настройка [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для запуска клиента и сервера при выборе пункта **Начать отладку** в меню **Отладка**.  
  
 Если служба WCF является резидентной внутри или является процессом, который не может быть запущен таким же образом, как служба NT, использовать этот метод нельзя. Вместо этого можно выполнить одно из следующих действий:  
  
-   Вручную присоединить отладчик к главному процессу. Дополнительные сведения см. в разделе [подключиться к процессам, под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     Или...  
  
-   Начать отладку клиента, а затем сделать шаг с заходом в вызов службы. Для этого необходимо включить отладку в файле app.config file. Дополнительные сведения [ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Запуск клиента и процесса размещения из Visual Studio  
  
1. Создайте решение [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], содержащее проекты клиента и сервера.  
  
2. Настройте решение для запуска клиентских и серверных процессов при выборе **Пуск** в меню **Отладка**.  
  
   1.  В **обозревателе решений** щелкните правой кнопкой мыши имя решения.  
  
   2.  Щелкните **Установка запускаемых проектов**.  
  
   3.  В диалоговом окне **Свойства \<имя> решения** выберите **Несколько запускаемых проектов**.  
  
   4.  В сетке **Несколько запускаемых проектов** на строке, соответствующей серверному проекту, щелкните **Действие** и выберите **Пуск**.  
  
   5.  На строке, соответствующей клиентскому проекту, щелкните **Действие** и выберите **Пуск**.  
  
   6.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также раздел  
 [Отладка служб WCF](../debugger/debugging-wcf-services.md)   
 [Ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Практическое руководство. Пошаговая отладка служб WCF](../debugger/how-to-step-into-wcf-services.md)