---
title: 'Практическое: отладка резидентной службы WCF | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
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
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec8f1fee46a1df931842992df1daa38942ca07bc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182251"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Практическое руководство. Отладка резидентной службы WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Объект *резидентная служба* — это служба WCF, которая не запускается внутри IIS, узла службы WCF, или [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server. Самый простой способ отладки резидентной WCF — Настройка [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для запуска сервера и клиента, при выборе **начать отладку** на **Отладка** меню.  
  
 Если служба WCF является резидентной внутри или является процессом, который не может быть запущен таким же образом, как служба NT, использовать этот метод нельзя. Вместо этого можно выполнить одно из следующих действий:  
  
-   Вручную присоединить отладчик к главному процессу. Дополнительные сведения см. в разделе [подключиться к процессам, под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     Или...  
  
-   Начать отладку клиента, а затем сделать шаг с заходом в вызов службы. Для этого необходимо включить отладку в файле app.config file. Дополнительные сведения [ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Запуск клиента и процесса размещения из Visual Studio  
  
1.  Создайте решение [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], содержащее проекты клиента и сервера.  
  
2.  Настройте решение для запуска клиентских и серверных процессов при выборе **запустить** на **Отладка** меню.  
  
    1.  В **обозревателе решений**, щелкните правой кнопкой мыши имя решения.  
  
    2.  Нажмите кнопку **назначение автозагружаемых проектов**.  
  
    3.  В **решение \<имя > свойства** выберите **несколько запускаемых проектов**.  
  
    4.  В **несколько запускаемых проектов** сетке на строке, соответствующей серверному проекту, щелкните **действие** и выберите **запустить**.  
  
    5.  В строке, соответствующей клиентскому проекту, щелкните **действие** и выберите **запустить**.  
  
    6.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Отладка служб WCF](../debugger/debugging-wcf-services.md)   
 [Ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Практическое руководство. Пошаговая отладка служб WCF](../debugger/how-to-step-into-wcf-services.md)



