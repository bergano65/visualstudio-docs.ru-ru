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
ms.openlocfilehash: 15792a8ecbc538bdbf5516d480abde4903fbd8d3
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304888"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging-c-visual-basic-f"></a>Практическое: указание версии платформы .NET Framework для отладки (C#, Visual Basic, F#)

Отладчик Visual Studio поддерживает отладку более старых версий Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] и текущей версии. Если запускать приложение из Visual Studio, отладчик всегда может определить правильную версию платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] для отлаживаемого приложения. Тем не менее, если приложение уже работает и его запуске отладки нажатием клавиши **присоединить к**, отладчик не всегда можно определить более старой версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. В этом случае появится сообщение об ошибке следующего содержания:  

``` cmd 
The debugger has made an incorrect assumption about the [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] version your application is going to use.  
```

В редких случаях, где отображается эта ошибка можно задать раздел реестра для указания отладчику, какую версию использовать.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Указание версии платформы .NET Framework для отладки  
  
1. Перейдите в каталог "Windows\Microsoft.NET\Framework" и посмотрите, какие версии платформы .NET Framework установлены на компьютере. Номера версий выглядят примерно так:  
  
    `V1.1.4322`  
  
    Определите правильный номер версии и запомните или запишите его.  
  
2. Запустите **Редактор реестра** (regedit).  
  
3. В **редакторе реестра** откройте папку HKEY_LOCAL_MACHINE.  
  
4. Перейдите в HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
    Если раздел не существует, щелкните правой кнопкой мыши HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine и выберите команду **Создать раздел**. Назовите новый раздел `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5. После перехода к {449EC4CC-30D2-4032-9256-EE18EB41B62B}, найдите в столбце **Имя** ключ "CLRVersionForDebugging".  
  
   1.  Если раздел не существует, щелкните правой кнопкой мыши {449EC4CC-30D2-4032-9256-EE18EB41B62B} и выберите команду **Создать строковый параметр**. Щелкните правой кнопкой мыши новый строковый параметр, нажмите кнопку **Переименовать**и тип `CLRVersionForDebugging`.  
  
6. Дважды щелкните **CLRVersionForDebugging**.  
  
7. В поле **Изменение строки** введите номер версии платформы .NET Framework в поле **Значение**. Например, "V1.1.4322".  
  
8. Нажмите кнопку **ОК**.  
  
9. Закройте **Редактор реестра**.  
  
     Если при запуске отладки по-прежнему возникает сообщение об ошибке, проверьте, что в реестре введен правильный номер версии. Также убедитесь, что используется поддерживаемая Visual Studio версия платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Отладчик совместим с текущей версией платформы .NET Framework и предыдущими версиями, но может не обладать прямой совместимостью с будущими версиями.  
  
## <a name="see-also"></a>См. также  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)