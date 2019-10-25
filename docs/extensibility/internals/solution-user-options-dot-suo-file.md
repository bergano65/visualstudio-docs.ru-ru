---
title: Пользовательские параметры решения (. Suo), файл | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f21e4a4a6530692709247e64b0d84aa7b06eb3a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723811"
---
# <a name="solution-user-options-suo-file"></a>Файл параметров пользователя решения (SUO-файл)
Файл параметров пользователя решения (. suo) содержит параметры решения "на пользователя". Этот файл не должен быть возвращен в систему управления исходным кодом.

 Файл пользовательских параметров решения (SUO) представляет собой структурированное хранилище или составной файл, хранящийся в двоичном формате. Сведения о пользователе сохраняются в потоках с именем, которое является ключом, который будет использоваться для обнаружения информации в SUO. Файл параметров пользователя решения используется для хранения параметров настройки пользователя и создается автоматически при сохранении решения в Visual Studio.

 Когда среда открывает suo-файл, она перечисляет все загруженные пакеты VSPackage. Если пакет VSPackage реализует интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>, среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> в VSPackage, запрашивающий загрузку всех своих данных из файла SUO.

 Это обязанность VSPackage, чтобы узнать, какие потоки были записаны в suo-файл. Для каждого потока, который он написал, пакет VSPackage обращается к среде с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>, чтобы загрузить определенный поток, определяемый ключом, который является именем потока. Затем среда выполняет обратный вызов VSPackage, чтобы считать конкретный поток, передающий имя потока, и указатель `IStream` в метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>.

 На этом этапе выполняется еще один вызов `LoadUserOptions`, чтобы узнать, есть ли еще один раздел suo-файла, который требуется считать. Этот процесс продолжится до тех пор, пока все потоки данных в файле SUO не будут считаны и обработаны средой.

 При сохранении или закрытии решения среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> с указателем на метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>. @No__t_0, содержащий двоичные данные для сохранения, передается методу <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>, который затем записывает сведения в suo-файл и вызывает метод `SaveUserOptions` еще раз, чтобы проверить наличие другого потока данных для записи в suo-файл.

 Эти два метода, `SaveUserOptions` и `WriteUserOptions`, вызываются рекурсивно для каждого потока данных, сохраняемых в файле SUO, передавая указатель на `IVsSolutionPersistence`. Они вызываются рекурсивно, чтобы разрешить запись нескольких потоков в файл. suo. Таким образом, сведения о пользователе сохраняются в решении и гарантированно будут в следующий раз при открытии решения.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Решения](../../extensibility/internals/solutions-overview.md)