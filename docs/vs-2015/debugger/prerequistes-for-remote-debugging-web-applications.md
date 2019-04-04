---
title: Условия для удаленной отладки веб-приложений | Документация Майкрософт
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
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1eda777fa335cc844eedc13f350aa44319f587fd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989250"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Условия для удаленной отладки веб-приложений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью отладчика [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно простым и понятным образом отладить веб-приложение как на локальном компьютере, так и на удаленном сервере. Это означает, что отладчик работает одинаково и предоставляет одни и те же возможности на любом компьютере. Однако для правильного выполнения удаленной отладки необходимо предварительно выполнить несколько условий.  
  
-   На сервере, на котором предполагается выполнять отладку, должны быть установлены компоненты удаленной отладки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [Настройка удаленной отладки](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
-   Рабочий процесс [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] по умолчанию выполняется в качестве пользовательского процесса ASPNET. Следовательно, для отладки приложения на компьютере, на котором выполняется [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], необходимо обладать правами администратора. Имя рабочего процесса [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] зависит от сценария отладки и версии IIS. Дополнительные сведения см. в разделе [Как найти имя процесса ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>См. также  
 [Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Требования к системе](../debugger/aspnet-debugging-system-requirements.md)
