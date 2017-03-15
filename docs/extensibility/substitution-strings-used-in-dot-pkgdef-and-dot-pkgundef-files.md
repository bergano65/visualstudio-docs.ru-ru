---
title: "Строки подстановки, используемые в. Pkgdef и. Файлы Pkgundef | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: c64a760b821663ba488f6f9dab415bad13d6047d
ms.lasthandoff: 02/22/2017

---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Строки подстановки, используемые в. Pkgdef и. Pkgundef файлы
Можно использовать перечисленные ниже в .pkgdef строки подстановки и .pkgundef файлы определения для Visual Studio изолированное приложение оболочки.  
  
## <a name="substitution-strings"></a>Строки подстановки  
  
|Строка|Описание|  
|------------|-----------------|  
|$=*RegistryEntry*$|Значение *RegistryEntry* запись. Если запись реестра строка заканчивается обратной косой чертой (\\), то используется значение по умолчанию раздела реестра. Например, подстановка строковые $= HKEY_CURRENT_USER\Environment\TEMP$ развернут к временной папке текущего пользователя.|  
|$AppName$|Полное имя приложения, которое передается AppEnv.dll точки входа. Полное имя состоит из имени приложения, подчеркивания и идентификатор класса (CLSID) объекта автоматизации приложения, который также записывается как значение параметра ThisVersionDTECLSID в pkgdef-файл проекта.|  
|$AppDataLocalFolder|Подпапки в папке % LOCALAPPDATA % для этого приложения.|  
|$BaseInstallDir$|Полный путь расположения, где установлен Visual Studio.|  
|$CommonFiles$|Значение переменной среды % CommonProgramFiles %.|  
|$MyDocuments$|Полный путь папки "Мои документы" текущего пользователя.|  
|$PackageFolder$|Полный путь в каталог, содержащий файлы пакета сборки для приложения.|  
|$ProgramFiles$|Значение переменной среды % ProgramFiles %.|  
|$RootFolder$|Полный путь к корневому каталогу приложения.|  
|$RootKey$|Корневой раздел реестра для приложения. По умолчанию используется корень HKEY_CURRENT_USER\Software\\*CompanyName*\\*ProjectName*\\*Номер_версии* (когда приложение работает, _Config добавляются в этот раздел). Оно задается значение RegistryRoot *имя_решения*pkgdef-файл.<br /><br /> Строка $RootKey$ можно использовать для извлечения значения реестра в подразделе приложения. Например, строка «$= $RootKey$ \AppIcon$» вернет значение записи AppIcon подраздел корневого приложения.<br /><br /> Средство синтаксического анализа последовательно обрабатывает pkgdef-файл и записи реестра в подраздел приложения доступны только в том случае, если элемент был ранее определен|  
|$ShellFolder$|Полный путь расположения, где установлен Visual Studio.|  
|$System$|В папку Windows\System32.|  
|$WINDIR$|В папке Windows.|  
  
 Если средство синтаксического анализа не распознает строки подстановки или он не может определить значение записи реестра или переменную среды, то он не выполняет подстановку эту часть строки.
