---
title: 'Ошибка: Не установлено средство ASP.NET | Документация Майкрософт'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 34ef8ef597c21230aa9ccdbd3146c07825753879
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680599"
---
# <a name="error-aspnet-not-installed"></a>Ошибка: не установлено средство ASP.NET
Ошибка возникает при неправильной установке [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] на компьютере, на котором выполняется отладка. Это означает, что либо [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] не было установлено вообще, либо [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] было установлено до установки служб IIS.

### <a name="to-reinstall-aspnet"></a>Переустановка ASP.NET

1. В окне командной строки введите следующую команду:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    где *версии* представляет номер версии платформы .NET Framework, установленной на компьютере, например v1.0.370. Можно определить версию платформы, просмотрев `\WINDOWS\Microsoft.NET\Framework` каталога.

   > [!NOTE]
   >  В Windows Server 2003 можно установить [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], используя элемент **Установка и удаление программ** на "Панели управления".

## <a name="see-also"></a>См. также раздел
- [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
