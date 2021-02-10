---
title: Отладка развернутых приложений ASP.NET | Документация Майкрософт
description: Использование Visual Studio для отладки развернутого приложения ASP.NET, подключив его к рабочему процессу и убедившись, что отладчик имеет доступ к символам для приложения.
ms.custom: SEO-VS-2020
ms.date: 06/30/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 9b298d756754743635fe3de10c8b72d3195ff3f8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872811"
---
# <a name="debugging-deployed-aspnet-applications"></a>Отладка развернутых приложений ASP.NET
Чтобы использовать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для отладки развернутого приложения, необходимо выполнить присоединение к рабочему процессу [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] и убедиться в том, что отладчик имеет доступ к символам для приложения. Кроме того, необходимо найти и открыть исходные файлы для данного приложения. См. сведения об [определении файлов символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [ поиске имени процесса ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md) и [требованиях к системе](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> Если выполнить присоединение к рабочему процессу [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] для отладки и установки точки останова, весь управляемый код процесса остановится. Прекращение выполнения всего управляемого кода в рабочем процессе может привести к остановке работы для всех пользователей сервера. Перед отладкой рабочего сервера примите во внимание потенциальное воздействие на рабочий сервер.

Процесс для присоединения к рабочему процессу [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] аналогичен процессу присоединения к любым другим удаленным процессам. После присоединения, если соответствующий проект не открыт, при остановке приложения появляется диалоговое окно. Это диалоговое окно запрашивает расположение исходных файлов для приложения. Имя файла, указанное в диалоговом окне, должно соответствовать имени файла, заданному в отладочных символах на веб-сервере. См. сведения о [присоединении к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). См. сведения о [настройке удаленной отладки ASP.NET на удаленном компьютере IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Во многих веб-приложениях [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] имеются ссылки на библиотеки DLL, содержащие бизнес-логику или другой полезный код. Такая ссылка копирует библиотеку DLL с локального компьютера в папку \bin виртуального каталога веб-приложения при развертывании приложения. При выполнении отладки помните, что веб-приложение ссылается на данную копию библиотеки DLL, а не на копию, находящуюся на локальном компьютере.

## <a name="see-also"></a>См. также
- [Отладка приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Практическое руководство. Включение отладки для приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Практическое руководство. Поиск имени процесса ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)