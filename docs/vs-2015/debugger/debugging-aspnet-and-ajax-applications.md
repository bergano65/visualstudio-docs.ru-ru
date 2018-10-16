---
title: Отладка приложений ASP.NET и AJAX | Документация Майкрософт
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
- debugging ASP.NET Web applications
- debugging [ASP.NET], about ASP.NET debugging
- WCF, debugging
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5943b75513394b44d88dfcfa496e56dad267171
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205209"
---
# <a name="debugging-aspnet-and-ajax-applications"></a>Отладка приложений ASP.NET и AJAX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Отладка веб-приложений [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] подобна отладке приложений Windows Form или отладке любого другого приложения Windows, поскольку оба типа приложений содержат элементы управления и события. Однако существуют основные различия между двумя типами приложений:  
  
-   Выполнять отслеживание состояния более сложно, чем в веб-приложении.  
  
-   В приложениях Windows код для отладки в большинстве случаев расположен в одном месте. В веб-приложениях код может быть расположен на клиенте или на сервере. Если код [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] полностью расположен на сервере, то код JavaScript или [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] может быть расположен на клиенте.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Подготовка к отладке ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Описаны шаги, которые необходимы для включения отладки приложений [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
 [Отладка веб-приложений](../debugger/debugging-web-applications.md)  
 Обсуждение отладки приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], включая приложения скриптов с включенной технологией Ajax.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)  
 Объясняется, почему для отладки исключений [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] должен быть включен режим "Только мой код".  
  
 [Debugging and Tracing Ajax Applications Overview](http://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)  
 Обсуждаются некоторые методы и средства, которые могут помочь в отладке кода AJAX.  
  
 [IntelliTrace](../debugger/intellitrace.md)  
 Ускорение отладки кода за счет использования IntelliTrace для ведения и просмотра журнала состояний приложения без необходимости частого перезапуска приложения. Возможность просматривать информацию о событиях и вызовах, произошедших во время выполнения приложения, и возможность запускать отладку, начиная с этих моментов времени. Доступно только в Visual Studio Ultimate.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отладка веб-приложений и скриптов](../debugger/debugging-web-applications-and-script.md)   
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Основы отладки](../debugger/debugger-basics.md)



