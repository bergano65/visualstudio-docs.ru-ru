---
title: 'Ошибка: ASP.NET не установлен | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2198ed401f714353be2dd18846dd527cc433e695
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843097"
---
# <a name="error-aspnet-not-installed"></a>Ошибка: не установлено средство ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ошибка возникает при неправильной установке [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] на компьютере, на котором выполняется отладка. Это означает, что либо [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] не было установлено вообще, либо [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] было установлено до установки служб IIS.  
  
### <a name="to-reinstall-aspnet"></a>Переустановка ASP.NET  
  
1. В окне командной строки введите следующую команду:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     *version* представляет номер версии платформы .NET Framework, установленной на данном компьютере, например v1.0.370. Можно определить версию платформы в каталоге `\WINDOWS\Microsoft.NET\Framework`.  
  
    > [!NOTE]
    > В Windows Server 2003 можно установить [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], используя элемент **Установка и удаление программ** на "Панели управления".  
  
## <a name="see-also"></a>См. также:  
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
