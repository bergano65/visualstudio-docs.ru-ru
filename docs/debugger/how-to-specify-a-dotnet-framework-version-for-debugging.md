---
title: 'Практическое: указание версии платформы .NET Framework для отладки | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 79bbe6e6feefa8e7ccab04fe5bae5c2ec7c214ae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902962"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Практическое руководство. Установка версии платформы .NET Framework для отладки
Отладчик [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] поддерживает отладку как текущей версии платформы Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], так и старых версий платформы. При запуске приложения из Visual Studio, отладчик всегда может определить правильную версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] для отладки приложения. Если приложение уже выполняется и используется **присоединить к**, отладчик не всегда можно определить более старой версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. В этом случае появится сообщение об ошибке следующего содержания:  
  
 Отладчик сделал неверное предположение о версии платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], которую приложение собирается использовать.  
  
 В этих редких случаях можно установить раздел реестра для указания отладчику, какую версию использовать.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Указание версии платформы .NET Framework для отладки  
  
1. Перейдите в каталог "Windows\Microsoft.NET\Framework" и посмотрите, какие версии платформы .NET Framework установлены на компьютере. Номера версий выглядят примерно так:  
  
    `V1.1.4322`  
  
    Определите правильный номер версии и запомните или запишите его.  
  
2. Запуск **редактора реестра** (regedit).  
  
3. В **редактора реестра**, откройте папку HKEY_LOCAL_MACHINE.  
  
4. Перейдите к: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
    Если ключ не существует, щелкните правой кнопкой мыши HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine и нажмите кнопку **новый ключ**. Назовите новый раздел `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5. После перехода к {449EC4CC-30D2-4032-9256-EE18EB41B62B}, найдите **имя** столбец и найти ключ "CLRVersionForDebugging".  
  
   1.  Если ключ не существует, щелкните правой кнопкой мыши {449EC4CC-30D2-4032-9256-EE18EB41B62B} и нажмите кнопку **новый строковый параметр**. Щелкните правой кнопкой мыши новый строковый параметр, нажмите кнопку **Переименовать**и тип `CLRVersionForDebugging`.  
  
6. Дважды щелкните **CLRVersionForDebugging**.  
  
7. В **Изменение строкового** введите номер версии платформы .NET Framework в **значение** поле. Например, "V1.1.4322".  
  
8. Нажмите кнопку **ОК**.  
  
9. Закрыть **редактора реестра**.  
  
     Если при запуске отладки по-прежнему возникает сообщение об ошибке, проверьте, что в реестре введен правильный номер версии. Также убедитесь, что используется поддерживаемая Visual Studio версия платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Отладчик совместим с текущей версией платформы .NET Framework и предыдущими версиями, но может не обладать прямой совместимостью с будущими версиями.  
  
## <a name="see-also"></a>См. также  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)