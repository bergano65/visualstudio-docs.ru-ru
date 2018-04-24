---
title: 'Ошибка: Не установлено средство ASP.NET | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: b462c3ed02ebd622a39cd08039037b3ba63e7f57
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="error-aspnet-not-installed"></a>Ошибка: не установлено средство ASP.NET
Ошибка возникает при неправильной установке [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] на компьютере, на котором выполняется отладка. Это означает, что либо [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] не было установлено вообще, либо [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] было установлено до установки служб IIS.  
  
### <a name="to-reinstall-aspnet"></a>Переустановка ASP.NET  
  
1.  В окне командной строки введите следующую команду:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     где *версии* представляет номер версии платформы .NET Framework, установленной на компьютере, например v1.0.370. Можно определить версию платформы, проверив `\WINDOWS\Microsoft.NET\Framework` каталога.  
  
    > [!NOTE]
    >  В Windows Server 2003 можно установить [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] с помощью **Установка и удаление программ** панели управления.  
  
## <a name="see-also"></a>См. также  
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)