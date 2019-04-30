---
title: Отладка приложений ASP.NET развернутой | Документация Майкрософт
ms.date: 06/30/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: f911cafb8ee0bdd341ce13c6eb38423ae4d3f473
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399394"
---
# <a name="debugging-deployed-aspnet-applications"></a>Отладка приложений ASP.NET, развернутых
Чтобы использовать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для отладки развернутого приложения, необходимо выполнить присоединение к рабочему процессу [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] и убедиться в том, что отладчик имеет доступ к символам для приложения. Кроме того, необходимо найти и открыть исходные файлы для данного приложения. Дополнительные сведения см. в разделе [Указание файлов символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [как: Поиск имени процесса ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md), и [требования к системе](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> При присоединении к [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] рабочий процесс для отладки и попадание в точку останова, весь управляемый код процесса останавливается. Прекращение выполнения всего управляемого кода в рабочем процессе может привести к остановке работы для всех пользователей сервера. Перед отладкой рабочего сервера примите во внимание потенциальное воздействие на рабочий сервер.

Процесс для присоединения к рабочему процессу [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] аналогичен процессу присоединения к любым другим удаленным процессам. После присоединения, если соответствующий проект не открыт, при остановке приложения появляется диалоговое окно. Это диалоговое окно запрашивает расположение исходных файлов для приложения. Имя файла, указанное в диалоговом окне, должно соответствовать имени файла, заданному в отладочных символах на веб-сервере. Дополнительные сведения см. в разделе [подключиться к процессам, под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Чтобы настроить удаленную отладку на сервере IIS, см. в разделе [Remote Debugging ASP.NET на удаленном компьютере IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Во многих веб-приложениях [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] имеются ссылки на библиотеки DLL, содержащие бизнес-логику или другой полезный код. Такая ссылка копирует библиотеку DLL с локального компьютера в папку \bin виртуального каталога веб-приложения, при развертывании приложения. При выполнении отладки помните, что веб-приложение ссылается на данную копию библиотеки DLL, а не на копию, находящуюся на локальном компьютере.

## <a name="see-also"></a>См. также
- [Отладка приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Практическое руководство. Включение отладки для приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Практическое руководство. Поиск имени процесса ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)