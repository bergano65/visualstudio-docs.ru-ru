---
title: "Служебная программа CreatePkgDef | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Определение пакета"
  - "Создание pkgdef"
  - "pkgdef"
  - "Createpkgdef"
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Служебная программа CreatePkgDef
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Принимает DLL\-файла для расширения Visual Studio как параметр и создает файл pkgdef прилагаются DLL\-файл. Pkgdef\-файл содержит все сведения, в противном случае будут записаны в системный реестр после установки расширения.  
  
> [!NOTE]
>  Большинство шаблонов проектов, которые включены в пакет SDK для Visual Studio автоматически создать .pkgdef файлы как часть процесса построения. Данный документ предназначен для тех, кому требуется создание пакетов вручную или преобразовывать существующие пакеты для использования .pkgdef развертывания.  
  
## Синтаксис  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## Аргументы  
 \/ out \=`FileName`  
 Обязательный. Задает имя выходного файла .pkgdef для```FileName`.  
  
 \/codebase  
 Необязательный. Принудительная регистрация с помощью служебной программы CodeBase.  
  
 \/ Assembly  
 Принудительная регистрация с помощью служебной программы сборки.  
  
 `AssemblyPath`  
 Путь к DLL\-файла, из которого вы хотите создать .pkgdef.  
  
## Заметки  
 Развертывание расширения с помощью файлов .pkgdef заменяет реестром более ранних версий Visual Studio.  
  
 Файлы .pkgdef должны устанавливаться в одном из следующих мест: %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\ или % vsinstalldir%\\Common7\\IDE\\Extensions\\. Если папка установки %localappdata%\\Microsoft\\Visual Studio\\14.0\\Extensions\\, расширение распознанные Visual Studio, но будет отключена по умолчанию. Пользователь может включить расширение с помощью **расширения и обновления**. Если устанавливается в папку % vsinstalldir%\\Common7\\IDE\\Extensions\\, расширение будет включено по умолчанию.  
  
> [!NOTE]
>  **Расширения и обновления** средство не может использоваться для доступа к расширение, если он установлен как часть пакета VSIX.  
  
## См. также  
 [Служебная программа CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)