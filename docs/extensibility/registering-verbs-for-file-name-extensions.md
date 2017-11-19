---
title: "Регистрация команд для расширений имен файлов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f430486c613e6281404110d4441d2a3d2100534
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="registering-verbs-for-file-name-extensions"></a>Регистрация команд для расширений имен файлов
Сопоставление расширения имени файла с помощью приложения обычно имеет предпочтительный действие, которое возникает, когда пользователь дважды щелкает файл. Этот предпочитаемый действия, связанные с глагола, например открытие, соответствующее действие.  
  
 Вы можете зарегистрировать команд, связанных с программный идентификатор (ProgID) для расширения с помощью оболочки ключ, указанный в раздел HKEY_CLASSES_ROOT\\*progid*\shell. Дополнительные сведения см. в разделе [типы файлов](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>Регистрация стандартных команд  
 Операционная система распознает следующие стандартные команды:  
  
-   Открыть  
  
-   Правка  
  
-   Воспроизвести  
  
-   Print  
  
-   Предварительный просмотр  
  
 Когда это возможно, регистрация обычного глагола. Наиболее распространенным вариантом является командой Open. Используйте команду редактирования только в том случае, если есть различие между при открытии файла и изменения файла. Например открытие htm-файл будут отображены его в браузере, а изменение htm-файл запускается редактор HTML. Стандартные команды локализованы с языком операционной системы.  
  
> [!NOTE]
>  При регистрации стандартных команд, не задано значение по умолчанию для открытых ключей. Значение по умолчанию содержит отображение строки меню. Операционная система предоставляет этой строки для стандартных команд.  
  
 Файлы проекта должен быть зарегистрирован для запуска нового экземпляра [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] при открытии файла. В следующем примере демонстрируется регистрация обычного глагола для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] проекта.  
  
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
  
 Чтобы открыть файл в существующий экземпляр [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], зарегистрируйте ключ DDEEXEC. В следующем примере демонстрируется регистрация обычного глагола для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] CS-файл.  
  
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
  
## <a name="setting-the-default-verb"></a>Настройка действия по умолчанию  
 Действия по умолчанию — действие, которое выполняется, когда пользователь дважды щелкает файл в проводнике Windows. Действия по умолчанию — это команда, указанный в качестве значения по умолчанию для HKEY_CLASSES_ROOT\\*progid*\Shell ключа. Если значение не указано, действия по умолчанию является первой команды, указанной в раздел HKEY_CLASSES_ROOT\\*progid*\Shell список ключей.  
  
> [!NOTE]
>  Если планируется изменить команду по умолчанию для расширения в развертывании side-by-side учесть влияние на установку и удаление. Во время установки исходного значения по умолчанию будет перезаписан.  
  
## <a name="see-also"></a>См. также  
 [Управление параллельными сопоставлениями файлов](../extensibility/managing-side-by-side-file-associations.md)