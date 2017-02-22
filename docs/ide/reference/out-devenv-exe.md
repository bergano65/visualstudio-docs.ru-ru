---
title: "/Out (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/out - параметр Devenv"
  - "построения [Visual Studio], ошибки"
  - "построения [Visual Studio], журналы"
  - "Devenv, /out - параметр"
  - "журналы ошибок [Visual Studio]"
  - "журналы ошибок [Visual Studio], ошибки при построении из командной строки"
  - "ошибки [Visual Studio], сборки"
  - "out - параметр Devenv"
  - "выходные файлы, ошибки построения"
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Out (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Указание файла, который будет использоваться для сохранения и отображения ошибок при выполнении, построении, повторном построении или развертывании решения.  
  
## Синтаксис  
  
```  
devenv /out FileName  
```  
  
## Аргументы  
 `FileName`  
 Обязательный.  Путь и имя файла для записи ошибок во время построения исполняемого файла.  
  
## Заметки  
 Если указано имя несуществующего файла, файл создается автоматически.  Если файл уже существует, то результаты добавляются в конец существующего содержимого этого файла.  
  
 Ошибки построения с использованием командной строки отображаются в окне **Команда** и в панели построителя решений окна **Выходные данные**.  Данный параметр удобен, если выполняются автоматические построения, и необходимо просматривать результаты.  
  
## Пример  
 В приведенном примере выполняется построение решения `MySolution`, а ошибки записываются в файл `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)