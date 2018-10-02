---
title: Условия для удаленной отладки веб-приложений | Документация Майкрософт
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
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 197a6e9b433173f1de13e3506db79e7edf53bade
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562755"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Условия для удаленной отладки веб-приложений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [предварительные требования для удаленной отладки веб-приложений](https://docs.microsoft.com/visualstudio/debugger/prerequistes-for-remote-debugging-web-applications).  
  
С помощью отладчика [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно простым и понятным образом отладить веб-приложение как на локальном компьютере, так и на удаленном сервере. Это означает, что отладчик работает одинаково и предоставляет одни и те же возможности на любом компьютере. Однако для правильного выполнения удаленной отладки необходимо предварительно выполнить несколько условий.  
  
-   На сервере, на котором предполагается выполнять отладку, должны быть установлены компоненты удаленной отладки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [Настройка удаленной отладки](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
-   Рабочий процесс [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] по умолчанию выполняется в качестве пользовательского процесса ASPNET. Следовательно, для отладки приложения на компьютере, на котором выполняется [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], необходимо обладать правами администратора. Имя рабочего процесса [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] зависит от сценария отладки и версии IIS. Дополнительные сведения см. в разделе [How to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>См. также  
 [Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Требования к системе](../debugger/aspnet-debugging-system-requirements.md)



