---
title: "Регистрация команды для расширений имен файлов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "команды, регистрация"
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Регистрация команды для расширений имен файлов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Сопоставление расширения имени файла с приложением, как правило, используется основной действие, которое происходит, когда пользователь дважды щелкает файл. Это предпочтительное связанного действия команды, например открытым, соответствующее действие.  
  
 Можно зарегистрировать команд, связанных с программный идентификатор \(ProgID\) для расширения с помощью оболочки ключ находится в этого*progid*\\shell. Дополнительные сведения см. в разделе [типы файлов](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## Регистрация стандартных команд  
 Операционная система распознает следующие стандартные команды:  
  
-   Открыть  
  
-   Правка  
  
-   Воспроизвести  
  
-   Печать  
  
-   Предпросмотр  
  
 Когда это возможно, регистрация стандартных команд. Наиболее распространенным вариантом является командой Open. Используйте команду редактирования только в том случае, если существует различие между Открытие файла и редактирования файла. Например откройте htm\-файл будут отображены его в браузере, а редактирование htm\-файл запускает редактор HTML. Стандартные команды локализованы с языковым стандартом операционной системы.  
  
> [!NOTE]
>  При регистрации стандартных команд, не задано значение по умолчанию для открытый ключ. Значение по умолчанию содержит отображаемую строку меню. Операционная система предоставляет этой строки для стандартных команд.  
  
 Файлы проекта должен быть зарегистрирован на запуск нового экземпляра [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] при открытии файла. В следующем примере показан стандартный глагол регистрацию для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] проекта.  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 Чтобы открыть файл в существующий экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], зарегистрируйте ключ DDEEXEC. В следующем примере показан стандартный глагол регистрацию для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] CS\-файл.  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## Настройка действия по умолчанию  
 Команда по умолчанию — действие, которое выполняется, когда пользователь дважды щелкает файл в проводнике Windows. Команда по умолчанию — это команда, указанный как значение по умолчанию для этого*progid*\\Shell ключа. Если значение не указано, команда по умолчанию является первой команды, указанной в этого*progid*\\Shell список ключей.  
  
> [!NOTE]
>  Если планируется изменить команду по умолчанию для расширения в развертывании side\-by\-side Учитывайте влияние на установки и удаления. Во время установки исходного значения по умолчанию будет перезаписан.  
  
## См. также  
 [Creating a File Association](_win32_file_associations)   
 [Управление сопоставлениями файлов Side\-by\-Side](../extensibility/managing-side-by-side-file-associations.md)