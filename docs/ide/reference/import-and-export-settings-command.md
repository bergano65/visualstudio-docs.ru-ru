---
title: "Команда Import and Export Settings | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Tools.ImportandExportSettings"
helpviewer_keywords: 
  - "Tools.ImportandExportSettings"
  - "Импорт и экспорт параметров - команда"
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Команда Import and Export Settings
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Импорт, экспорт или сброс параметров [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Синтаксис  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## Переключатели  
 \/export:`filename`  
 Необязательный.  Экспорт текущих параметров в указанный файл.  
  
 \/import:`filename`  
 Необязательный.  Импорт параметров из указанного файла.  
  
 \/reset  
 Необязательный.  Сброс текущих параметров.  
  
## Заметки  
 При выполнении этой команды без переключателей открывается мастер **импорта и экспорта параметров**.  Дополнительные сведения см. в разделе [How to: Share Settings Between Computers or Visual Studio Versions](http://msdn.microsoft.com/ru-ru/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## Пример  
 Приведенная ниже команда выполняет экспорт текущих параметров в файл `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## См. также  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)