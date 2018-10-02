---
title: Строки подстановки, используемые в. Pkgdef и. Файлы Pkgundef | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24996e4e32ab86af46fce5280947719f906ffc3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571694"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Строки подстановки, используемые в. Pkgdef и. Файлы Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [использовать строки подстановки в. Pkgdef и. Файлы Pkgundef](https://docs.microsoft.com/visualstudio/extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files).  
  
Вы можете использовать строки подстановки, перечислены ниже в .pkgdef и .pkgundef файлы определения для Visual Studio приложения isolated shell.  
  
## <a name="substitution-strings"></a>Строки подстановки  
  
|String|Описание|  
|------------|-----------------|  
|$=*RegistryEntry*$|Значение *RegistryEntry* запись. Если запись реестра строка заканчивается обратной косой чертой (\\), то используется значение по умолчанию раздела реестра. Например, подстановка строковые $= HKEY_CURRENT_USER\Environment\TEMP$ расширяется для временной папке текущего пользователя.|  
|$AppName$|Полное имя приложения, которое передается AppEnv.dll точек входа. Полное имя состоит из имени приложения, подчеркивания и идентификатор класса (CLSID) объекта автоматизации приложения, который также записывается как значение параметра ThisVersionDTECLSID в pkgdef-файл проекта.|  
|$AppDataLocalFolder|Подпапки в папке % LOCALAPPDATA % для этого приложения.|  
|$BaseInstallDir$|Полный путь к расположению, в котором была установлена Visual Studio.|  
|$CommonFiles$|Значение переменной среды % CommonProgramFiles %.|  
|$MyDocuments$|Полный путь к папке «Мои документы» текущего пользователя.|  
|$PackageFolder$|Полный путь к каталогу, содержащему файлы сборки пакета для приложения.|  
|$ProgramFiles$|Значение переменной среды % ProgramFiles %.|  
|$RootFolder$|Полный путь к корневой каталог приложения.|  
|$RootKey$|Корневой раздел реестра для приложения. По умолчанию, используется корень HKEY_CURRENT_USER\Software\\*CompanyName*\\*имя_проекта*\\*VersionNumber* (когда приложения, _Config добавляется к этому ключу). Оно задается значение RegistryRoot *SolutionName*pkgdef-файл.<br /><br /> Строка $ $RootKey можно использовать для извлечения значения реестра в подразделе приложения. Например, строка «$= $RootKey$ \AppIcon$» возвратит значение записи AppIcon корневого раздела приложения.<br /><br /> Средство синтаксического анализа последовательно обрабатывает pkgdef-файл и доступ к записи реестра в подраздел приложения только в том случае, если запись было определено ранее|  
|$ShellFolder$|Полный путь к расположению, в котором была установлена Visual Studio.|  
|$System$|В папку Windows\system32.|  
|$WINDIR$|Папка Windows.|  
  
 Если средство синтаксического анализа не распознает строку подстановки, или он не может определить значение записи реестра или переменную среды, то он не выполняет подстановку в этой части строки.

