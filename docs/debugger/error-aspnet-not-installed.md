---
title: "Ошибка: не установлено средство ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.http_not_supported"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET, сообщения об ошибках установки"
  - "отладчик, ошибки веб-приложения"
  - "сообщения об ошибках, ASP.NET"
  - "в веб-приложениях, ошибки"
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ошибка: не установлено средство ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ошибка возникает при неправильной установке [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] на компьютере, на котором выполняется отладка.  Это означает, что либо [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] не было установлено вообще, либо [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] было установлено до установки служб IIS.  
  
### Переустановка ASP.NET  
  
1.  В окне командной строки введите следующую команду:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     где *version* представляет номер версии платформы .NET Framework, установленной на данном компьютере, например v1.0.370.  Можно определить версию платформы в каталоге `\WINDOWS\Microsoft.NET\Framework`.  
  
    > [!NOTE]
    >  В Windows Server 2003 можно установить [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], используя элемент **Установка и удаление программ** на "Панели управления".  
  
## См. также  
 [Отладка веб\-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)