---
title: Отладка развернутых веб-приложений | Документация Майкрософт
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
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d7b7a95af1922f5ad57d15fb53dcba561a9f139e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994217"
---
# <a name="debugging-deployed-web-applications"></a>Отладка развернутых веб-приложений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если необходимо выполнить отладку веб-приложения, которое выполняется на рабочем сервере, это необходимо делать с осторожностью. Если выполнить присоединение к рабочему процессу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], например, для отладки и установки точки останова, весь управляемый код процесса останавливается. Прекращение выполнения всего управляемого кода в рабочем процессе может привести к остановке работы для всех пользователей сервера. Перед отладкой рабочего сервера примите во внимание потенциальное воздействие на рабочий сервер.  
  
 Чтобы использовать [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для отладки развернутого приложения, необходимо выполнить присоединение к рабочему процессу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] и убедиться в том, что отладчик имеет доступ к символам для приложения. Кроме того, необходимо найти и открыть исходные файлы для данного приложения. Дополнительные сведения см. в разделе [Указание файлов символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [как: Поиск имени процесса ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md), и [требования к системе](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
>  Во многих веб-приложениях [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] имеются ссылки на библиотеки DLL, содержащие бизнес-логику или другой полезный код. Такая ссылка автоматически копирует библиотеку DLL с локального компьютера в папку \bin виртуального каталога веб-приложения. При выполнении отладки помните, что веб-приложение ссылается на данную копию библиотеки DLL, а не на копию, находящуюся на локальном компьютере.  
  
 Процесс для присоединения к рабочему процессу [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] аналогичен процессу присоединения к любым другим удаленным процессам. После присоединения, если соответствующий проект не открыт, при остановке приложения появляется диалоговое окно. Это диалоговое окно запрашивает расположение исходных файлов для приложения. Имя файла, указанное в диалоговом окне, должно соответствовать имени файла, заданному в отладочных символах на веб-сервере. Дополнительные сведения см. в разделе [подключиться к процессам, под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>См. также  
 [Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Отладка веб-приложений и скриптов](../debugger/debugging-web-applications-and-script.md)   
 [Практическое руководство. Включение отладки для приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Практическое руководство. Поиск имени процесса ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
