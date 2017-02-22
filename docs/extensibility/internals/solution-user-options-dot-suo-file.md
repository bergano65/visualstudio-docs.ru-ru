---
title: "Пользовательских параметров решения (. Файл SUO) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SUO-файлы, пакеты VSPackage"
  - "SUO-файлы, пакеты VSPackage"
  - "решения, SUO-файлы"
  - "решения, параметры пользователя"
  - "файл пользовательских параметров (.suo) решения"
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Пользовательских параметров решения (. Файл SUO)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Решения \(.suo\) в файле пользователя содержит параметры пользователя решения. Этот файл не проверяется в систему управления версиями.  
  
 Решения \(.suo\) в файле пользователя — это структурированное хранилище, или составным, файл хранится в двоичном формате. Сохранить сведения о пользователе в потоки с именем ключа, который будет использоваться для определения сведений в файле SUO выполняется поток. Файл пользовательских параметров решения используется для хранения параметров предпочтений пользователя и создается автоматически, когда Visual Studio сохраняет решение.  
  
 При открытии среды SUO\-файл перечисляет все загруженные пакеты VSPackage. Если VSPackage реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> интерфейс, а затем вызывает среды <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> метод VSPackage, попросите его для загрузки всех данных из SUO\-файл.  
  
 Это VSPackage обязан знать, что потоков, может записан в файл SUO. Для каждого потока, который он написал VSPackage выполняет обратный вызов к среде через <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> для загрузки определенного потока, определяемое ключом, который является имя потока. Среда вызывает пакет VSPackage для чтения этого конкретного потока, передавая имя потока и `IStream` указатель <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> метод.  
  
 На этом этапе другой вызов `LoadUserOptions` ли другой раздел SUO\-файл, имеющий для чтения. Этот процесс продолжается, пока все потоки данных в файле SUO чтения и обрабатываются средой.  
  
 При сохранении решения или закрыты, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> метод с указателем <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> метод.`IStream` Содержащий двоичные данные должны быть сохранены передается <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> метод, который записывает сведения об SUO\-файл и вызывает `SaveUserOptions` метод еще раз, чтобы увидеть, если другой поток данных для записи в файл SUO.  
  
 Эти два метода `SaveUserOptions` и `WriteUserOptions`, рекурсивно вызывается для каждого потока данных сохраняется в файле SUO, передав указатель на `IVsSolutionPersistence`. Они называются рекурсивно для написания множественные потоки для SUO\-файл. Таким образом сведения о пользователе сохраняется вместе с решением и гарантированно существует при следующем открытии решения.  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Решения](../../extensibility/internals/solutions.md)