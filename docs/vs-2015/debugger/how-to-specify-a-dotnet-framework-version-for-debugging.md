---
title: Практическое руководство. Указание версии платформы .NET Framework для отладки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4c785c419ead31ad90e2b20ae7f48af778598bb6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042770"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Практическое руководство. Указание версии платформы .NET Framework для отладки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Отладчик [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] поддерживает отладку как текущей версии платформы Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], так и старых версий платформы. Если запускать приложение из Visual Studio, отладчик всегда может определить правильную версию платформы [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] для отлаживаемого приложения. Если приложение уже выполняется и используется **присоединить к**, отладчик не всегда можно определить более старой версии [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. В этом случае появится сообщение об ошибке следующего содержания:  
  
 Отладчик сделал неверное предположение о версии платформы [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], которую приложение собирается использовать.  
  
 В этих редких случаях можно установить раздел реестра для указания отладчику, какую версию использовать.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Указание версии платформы .NET Framework для отладки  
  
1. Перейдите в каталог "Windows\Microsoft.NET\Framework" и посмотрите, какие версии платформы .NET Framework установлены на компьютере. Номера версий выглядят примерно так:  
  
     `V1.1.4322`  
  
     Определите правильный номер версии и запомните или запишите его.  
  
2. Запустите **Редактор реестра** (regedit).  
  
3. В **редакторе реестра** откройте папку HKEY_LOCAL_MACHINE.  
  
4. Перейдите к: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Если раздел не существует, щелкните правой кнопкой мыши HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine и выберите команду **Создать раздел**. Назовите новый раздел `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5. После перехода к {449EC4CC-30D2-4032-9256-EE18EB41B62B}, найдите в столбце **Имя** ключ "CLRVersionForDebugging".  
  
    1. Если раздел не существует, щелкните правой кнопкой мыши {449EC4CC-30D2-4032-9256-EE18EB41B62B} и выберите команду **Создать строковый параметр**. Щелкните правой кнопкой мыши новый строковый параметр, нажмите кнопку **Переименовать**и тип `CLRVersionForDebugging`.  
  
6. Дважды щелкните **CLRVersionForDebugging**.  
  
7. В поле **Изменение строки** введите номер версии платформы .NET Framework в поле **Значение**. Пример: V1.1.4322  
  
8. Нажмите кнопку **ОК**.  
  
9. Закройте **Редактор реестра**.  
  
     Если при запуске отладки по-прежнему возникает сообщение об ошибке, проверьте, что в реестре введен правильный номер версии. Также убедитесь, что используется поддерживаемая Visual Studio версия платформы [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Отладчик совместим с текущей версией платформы .NET Framework и предыдущими версиями, но может не обладать прямой совместимостью с будущими версиями.  
  
## <a name="see-also"></a>См. также  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)
