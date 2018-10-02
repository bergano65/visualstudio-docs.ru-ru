---
title: Пользовательских параметров решения (. SUO-) файл | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 408acad4031417f4c3dd70b49758f8bee8e2819d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560000"
---
# <a name="solution-user-options-suo-file"></a>Файл параметров пользователя решения (SUO-файл)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [пользовательских параметров решения (. SUO-) файл](https://docs.microsoft.com/visualstudio/extensibility/internals/solution-user-options-dot-suo-file).  
  
Решения (SUO-) в файле пользователя содержит параметры пользователя решения. Этот файл не следует проверять систему управления версиями.  
  
 Решения (SUO-) в файле пользователя — это структурированное хранилище, или составным, файл, хранящийся в двоичном формате. Сохранить сведения о пользователе в потоки с имя потока, что ключ, который будет использоваться для определения сведений в SUO-файл. Файл пользовательских параметров решения используется для хранения настройки параметров пользователя, а также создается автоматически, когда Visual Studio сохраняет решение.  
  
 Когда среде открывает файл SUO, он перечисляет всех загруженных пакетов VSPackage. Если VSPackage реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> интерфейс, то среда вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> метод VSPackage, попросите его для загрузки всех данных из SUO-файл.  
  
 Это в пакете VSPackage обязан знать, что потоков, наверняка приходилось писать в SUO-файл. Для каждого потока, который он написал, VSPackage вызывает обратно в среду через <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> для загрузки конкретного потока, который определяется с помощью ключа, которое является именем потока. Среды затем осуществляет обратный вызов VSPackage для чтения этого конкретного потока, передав имя потока и `IStream` указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> метод.  
  
 В этот момент другой вызов `LoadUserOptions` ли другой участок SUO-файл, имеющий для чтения. Этот процесс продолжается, пока все потоки данных в файл SUO были прочитаны и обрабатываются средой.  
  
 При сохранении или закрытии, среда вызывает метод решения <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> метод с указателем на <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> метод. `IStream` Содержащий двоичные данные для сохранения передается <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> метод, который затем будет записывать данные в файл SUO и вызовы `SaveUserOptions` метод, чтобы выяснить, имеется другой поток данных для записи .suo файл.  
  
 Эти два метода `SaveUserOptions` и `WriteUserOptions`, называются рекурсивно для каждого потока данных сохраняется в SUO-файл, передав указатель на `IVsSolutionPersistence`. Они называются рекурсивно, чтобы разрешить для записи нескольких потоков к SUO-файл. Таким образом сведения о пользователе сохраняется с помощью решения и гарантированно существует при следующем открытии решения.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Решения](../../extensibility/internals/solutions.md)

