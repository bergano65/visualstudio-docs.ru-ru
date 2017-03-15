---
title: "Практическое руководство. Установка версии платформы .NET Framework для отладки | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "платформа .NET Framework, указание версии для отладки"
  - "отладка [Visual Studio], указание версии платформы .NET Framework"
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Практическое руководство. Установка версии платформы .NET Framework для отладки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Отладчик [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] поддерживает отладку как текущей версии платформы Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], так и старых версий платформы.  Если запускать приложение из Visual Studio, отладчик всегда может определить правильную версию платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] для отлаживаемого приложения.  Если приложение уже выполняется и используется функция **Присоединиться к**, отладчик не всегда может определить старую версию платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  В этом случае появится сообщение об ошибке следующего содержания:  
  
 Отладчик сделал неверное предположение о версии платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], которую приложение собирается использовать.  
  
 В этих редких случаях можно установить раздел реестра для указания отладчику, какую версию использовать.  
  
### Указание версии платформы .NET Framework для отладки  
  
1.  Перейдите в каталог "Windows\\Microsoft.NET\\Framework" и посмотрите, какие версии платформы .NET Framework установлены на компьютере.  Номера версий выглядят примерно так:  
  
     `V1.1.4322`  
  
     Определите правильный номер версии и запомните или запишите его.  
  
2.  Запустите **Редактор реестра** \(regedit\).  
  
3.  В **Редакторе реестра** откройте папку HKEY\_LOCAL\_MACHINE.  
  
4.  Перейдите в HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine\\{449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}  
  
     Если раздел не существует, щелкните правой кнопкой мыши HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\8.0\\AD7Metrics\\Engine и выберите команду **Создать раздел**.  Имя раздела должно быть: `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  После перехода к {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}, найдите в столбце **Имя** ключ "CLRVersionForDebugging".  
  
    1.  Если раздел не существует, щелкните правой кнопкой мыши {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B} и выберите команду **Создать строковый параметр**.  Щелкните правой кнопкой мыши созданный строковый параметр, выберите **Переименовать** и введите `CLRVersionForDebugging`.  
  
6.  Дважды щелкните **CLRVersionForDebugging**.  
  
7.  В поле **Изменение строки** введите номер версии платформы .NET Framework в поле **Значение**.  Например, "V1.1.4322".  
  
8.  Нажмите кнопку **ОК**.  
  
9. Закройте **Редактор реестра**.  
  
     Если при запуске отладки по\-прежнему возникает сообщение об ошибке, проверьте, что в реестре введен правильный номер версии.  Также убедитесь, что используется поддерживаемая Visual Studio версия платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Отладчик совместим с текущей версией платформы .NET Framework и предыдущими версиями, но может не обладать прямой совместимостью с будущими версиями.  
  
## См. также  
 [Параметры отладки и подготовка](../debugger/debugger-settings-and-preparation.md)