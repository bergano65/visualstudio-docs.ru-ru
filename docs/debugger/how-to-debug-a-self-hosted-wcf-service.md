---
title: 'Практическое: отладка резидентной службы WCF | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 255ca0f7d472060d110135536d76de99dc46a18e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872126"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Практическое руководство. Отладка резидентной службы WCF
Объект *резидентная служба* — это служба WCF, которая не запускается внутри IIS, узла службы WCF, или [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server. Самый простой способ отладки резидентной WCF — Настройка [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для запуска сервера и клиента, при выборе **начать отладку** на **Отладка** меню.  
  
 Если служба WCF является резидентной внутри или является процессом, который не может быть запущен таким же образом, как служба NT, использовать этот метод нельзя. Вместо этого можно выполнить одно из следующих действий:  
  
-   Вручную присоединить отладчик к главному процессу. Дополнительные сведения см. в разделе [подключиться к процессам, под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     Или...  
  
-   Начать отладку клиента, а затем сделать шаг с заходом в вызов службы. Для этого необходимо включить отладку в файле app.config file. Дополнительные сведения [ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Запуск клиента и процесса размещения из Visual Studio  
  
1. Создайте решение [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], содержащее проекты клиента и сервера.  
  
2. Настройте решение для запуска клиентских и серверных процессов при выборе **запустить** на **Отладка** меню.  
  
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