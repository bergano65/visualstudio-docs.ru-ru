---
title: Регистрация команд для расширений имен файлов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dbd97310163a4eb3ae5502c6341dc73322ca653d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685272"
---
# <a name="registering-verbs-for-file-name-extensions"></a>Регистрация команд для расширений имен файлов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Сопоставление расширения имени файла с приложением обычно имеет предпочитаемое действие, которое происходит при двойном щелчке файла пользователем. Это предпочтительное действие связано с командой, например Open, которая соответствует действию.  
  
 Вы можете зарегистрировать команды, связанные с программным идентификатором (ProgID) для расширения, с помощью ключа оболочки, расположенного по адресу HKEY_CLASSES_ROOT \\ *ProgID*\шелл. Дополнительные сведения см. в разделе [типы файлов](https://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>Регистрация стандартных команд  
 Операционная система распознает следующие стандартные команды:  
  
- Открыть  
  
- Изменить  
  
- Воспроизведение  
  
- Печать  
  
- Предварительный просмотр  
  
  По возможности Зарегистрируйте стандартную команду. Наиболее распространенным выбором является команда Open. Используйте команду Edit, только если есть четкое различие между открытием файла и редактированием файла. Например, открытие HTM-файла отображает его в браузере, а редактирование HTM-файла запускает редактор HTML. Стандартные команды локализованы с локальными языками операционной системы.  
  
> [!NOTE]
> При регистрации стандартных команд не устанавливайте значение по умолчанию для открытого ключа. Значение по умолчанию содержит отображаемую строку в меню. Операционная система предоставляет эту строку для стандартных команд.  
  
 Файлы проекта должны быть зарегистрированы для запуска нового экземпляра, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] когда пользователь открывает файл. В следующем примере показана стандартная Регистрация команд для [!INCLUDE[csprcs](../includes/csprcs-md.md)] проекта.  
  
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
  
 Чтобы открыть файл в существующем экземпляре [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , зарегистрируйте ключ ддиксек. В следующем примере показана стандартная регистрация для CS- [!INCLUDE[csprcs](../includes/csprcs-md.md)] файла.  
  
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
  
## <a name="setting-the-default-verb"></a>Настройка глагола по умолчанию  
 Глагол по умолчанию — это действие, выполняемое, когда пользователь дважды щелкает файл в проводнике Windows. Глагол по умолчанию — это команда, указанная в качестве значения по умолчанию для HKEY_CLASSES_ROOT \\ *ProgID*\шелл Key. Если значение не указано, команда по умолчанию является первой командой, указанной в списке HKEY_CLASSES_ROOT \\ *ProgID*\шелл Key.  
  
> [!NOTE]
> Если вы планируете изменить глагол по умолчанию для расширения в параллельном развертывании, учитывайте влияние на установку и удаление. Во время установки исходное значение по умолчанию перезаписывается.  
  
## <a name="see-also"></a>См. также:  
 [Управление параллельными сопоставлениями файлов](../extensibility/managing-side-by-side-file-associations.md)
