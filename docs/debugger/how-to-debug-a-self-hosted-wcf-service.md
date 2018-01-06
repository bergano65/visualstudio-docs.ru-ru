---
title: "Как: отладки резидентной WCF службы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 004e4685af33a33248d3fab7c39504300de2ed95
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Практическое руководство. Отладка резидентной службы WCF
Объект *резидентная служба* является службой WCF, которая не запускается внутри IIS, узла службы WCF или [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server. Легкий путь отладки резидентной WCF — Настройка [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для запуска клиента и сервера при выборе **начать отладку** на **отладки** меню.  
  
 Если служба WCF является резидентной внутри или является процессом, который не может быть запущен таким же образом, как служба NT, использовать этот метод нельзя. Вместо этого можно выполнить одно из следующих действий:  
  
-   Вручную присоединить отладчик к главному процессу. Дополнительные сведения см. в разделе [присоединение к процессу под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     Или...  
  
-   Начать отладку клиента, а затем сделать шаг с заходом в вызов службы. Для этого необходимо включить отладку в файле app.config file. Для получения дополнительной информации [ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Запуск клиента и процесса размещения из Visual Studio  
  
1.  Создайте решение [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], содержащее проекты клиента и сервера.  
  
2.  Настройте решение для запуска клиентских и серверных процессов при выборе **запустить** на **отладки** меню.  
  
    1.  В **обозревателе решений**, щелкните правой кнопкой мыши имя решения.  
  
    2.  Нажмите кнопку **Установка автозагружаемых проектов**.  
  
    3.  В **решения \<имя > свойства** выберите **несколько запускаемых проектов**.  
  
    4.  В **несколько запускаемых проектов** сетке на строке, соответствующей серверному проекту, щелкните **действия** и выберите **запустить**.  
  
    5.  На строке, соответствующей клиентскому проекту, щелкните **действия** и выберите **запустить**.  
  
    6.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Отладка служб WCF](../debugger/debugging-wcf-services.md)   
 [Ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Практическое руководство. Пошаговая отладка служб WCF](../debugger/how-to-step-into-wcf-services.md)