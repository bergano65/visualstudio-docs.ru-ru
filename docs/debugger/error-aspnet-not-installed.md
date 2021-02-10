---
title: Не установлено средство ASP.NET
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 2388e59ae760e28c8f778ab8ccb15265414174b7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871758"
---
# <a name="error-aspnet-not-installed"></a>Ошибка: не установлено средство ASP.NET
Ошибка возникает при неправильной установке [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] на компьютере, на котором выполняется отладка. Это означает, что либо [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] не было установлено вообще, либо [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] было установлено до установки служб IIS.

### <a name="to-reinstall-aspnet"></a>Переустановка ASP.NET

1. В окне командной строки введите следующую команду:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    *version* представляет номер версии платформы .NET Framework, установленной на данном компьютере, например v1.0.370. Можно определить версию платформы в каталоге `\WINDOWS\Microsoft.NET\Framework`.

   > [!NOTE]
   > В Windows Server 2003 можно установить [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], используя элемент **Установка и удаление программ** на "Панели управления".

## <a name="see-also"></a>См. также
- [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
