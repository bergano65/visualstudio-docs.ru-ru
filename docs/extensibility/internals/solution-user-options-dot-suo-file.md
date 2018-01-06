---
title: "Пользовательских параметров решения (. Файл SUO) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0bca2eef930b871d5728ff1c85742a28f4b51a7e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="solution-user-options-suo-file"></a>Пользовательских параметров решения (. Файл SUO)
Решения (.suo) в файле пользователя содержит параметры пользователя решения. Этот файл не проверяется в систему управления версиями.  
  
 Решения (.suo) в файле пользователя — это структурированное хранилище, или составным, файлов, хранящихся в двоичном формате. Позволяет сохранить сведения о пользователе в потоки с имя потока, в которой ключ, который будет использоваться для идентификации информации в файл SUO. Файл пользовательских параметров решения используется для хранения параметров предпочтений пользователя и создается автоматически, когда Visual Studio сохраняет решения.  
  
 Если среды открывает файл SUO, то перечисляются все загруженные пакеты VSPackage. Если VSPackage реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> интерфейс, то среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> метод в VSPackage, попросите его для загрузки всех данных из SUO-файл.  
  
 Это VSPackage обязан знать, что создает поток может записан в файл SUO. Для каждого потока, который он написал, VSPackage обратный вызов в среду посредством <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> для загрузки конкретного потока, который определяется параметром ключ, который является имя потока. Среда вызывает пакет VSPackage для чтения этого конкретного потока, передав имя потока и `IStream` указатель <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> метод.  
  
 На этом этапе другой вызов `LoadUserOptions` ли другой раздел SUO-файл, имеющий для чтения. Этот процесс продолжается, пока все потоки данных в файл SUO чтения и обрабатываются средой.  
  
 При сохранении или закрытии среда вызывает метод решения <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> метод с указателем <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> метод. `IStream` Содержащий двоичные данные должны быть сохранены передается <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> метод, который затем будет записывать данные в файл SUO и вызовы `SaveUserOptions` метод, чтобы проверить, существует ли другой поток данных для записи .suo файл.  
  
 Эти два метода, `SaveUserOptions` и `WriteUserOptions`, рекурсивно вызывается для каждого потока данных сохраняется в файл SUO, передавая указатель `IVsSolutionPersistence`. Они называются рекурсивно для записи нескольких потоков для SUO-файл. Таким образом сведения о пользователе сохраняется вместе с решением и гарантированно существует при следующем открытии решения.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Решения](../../extensibility/internals/solutions.md)