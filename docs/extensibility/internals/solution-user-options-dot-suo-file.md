---
title: Параметры пользователя решения (. Суо) Файл Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9469663d3ac258e1c568778894d8584c68c13632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705316"
---
# <a name="solution-user-options-suo-file"></a>Файл параметров пользователя решения (SUO-файл)
Пользовательский файл решения (.suo) содержит параметры решения для пользователей. Этот файл не должен быть зарегистрирован в управлении исходным кодом.

 Пользовательский файл решения (.suo) представляет собой структурированное хранилище или соединение, хранящийся в двоичном формате. Вы сохраняете информацию о пользователе в потоки с именем потока, который будет использоваться для идентификации информации в файле .suo. Файл параметров пользователя решения используется для хранения настроек пользовательских предпочтений и создается автоматически, когда Visual Studio сохраняет решение.

 Когда среда открывает файл .suo, он перечисляет все загруженные в настоящее время VSPackages. Если VSPackage реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> интерфейс, то среда <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> вызывает метод на VSPackage с просьбой загрузить все свои данные из файла .suo.

 Обязанность VSPackage знать, какие потоки он мог бы записать в файл .suo. Для каждого потока, который он написал, VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> вызывает обратно в среду через для загрузки определенного потока, который определяется ключом, который является названием потока. Затем среда перезванивает VSPackage, чтобы прочитать этот конкретный `IStream` поток, передающий название потока, и указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> метод.

 В этот момент, другой `LoadUserOptions` вызов делается, чтобы увидеть, если есть еще один раздел файла .suo, который должен быть прочитан. Этот процесс продолжается до тех пор, пока все потоки данных в файле .suo не будут прочитаны и обработаны средой.

 Когда решение сохраняется или закрывается, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> с указателем на метод. Содержащий `IStream` двоичную информацию, которая <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> будет сохранена передается методу, который затем `SaveUserOptions` записывает информацию в файл .suo и вызывает метод снова, чтобы увидеть, есть ли другой поток информации, чтобы написать в файл .suo.

 Эти два метода, `SaveUserOptions` и, `WriteUserOptions`называются рекурсивно для каждого потока информации, которые будут сохранены в файл .suo, проходя в указатель на `IVsSolutionPersistence`. Они называются рекурсивно, чтобы для записи нескольких потоков в файл .suo. Таким образом, пользовательская информация сохраняется с помощью решения и гарантированно будет там в следующий раз, когда решение будет открыто.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Решения](../../extensibility/internals/solutions-overview.md)
