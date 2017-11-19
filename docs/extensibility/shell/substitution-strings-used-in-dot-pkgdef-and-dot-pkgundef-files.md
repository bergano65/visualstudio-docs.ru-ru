---
title: "Строки подстановки, используемые в. Pkgdef и. Файлы pkgundef-файлов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6144c0200c03776ead9e7dc7f46b5e9e707b6e82
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>Строки подстановки, используемые в. Pkgdef и. Файлы pkgundef-файлов
Можно использовать перечисленные ниже в .pkgdef строки подстановки и определение для Visual Studio файлы .pkgundef приложения isolated shell.  
  
## <a name="substitution-strings"></a>Строки подстановки  
  
|Строка|Описание|  
|------------|-----------------|  
|$=*RegistryEntry*$|Значение *RegistryEntry* входа. Если строка записи реестра заканчивается обратной косой чертой (\\), то используется значение по умолчанию раздела реестра. Например, подстановка строковые $= HKEY_CURRENT_USER\Environment\TEMP$ расширяется к временной папке текущего пользователя.|  
|$AppName$|Полное имя приложения, которое передается AppEnv.dll точек входа. Полное имя состоит из имени приложения, подчеркивания и идентификатор класса (CLSID) объекта автоматизации приложения, который также записывается как значение параметра ThisVersionDTECLSID в pkgdef-файл проекта.|  
|$AppDataLocalFolder|Вложенную папку в каталоге % LOCALAPPDATA % для этого приложения.|  
|$BaseInstallDir$|Полный путь расположения, где установлен Visual Studio.|  
|$CommonFiles$|Значение переменной среды % CommonProgramFiles %.|  
|$MyDocuments$|Полный путь папки «Мои документы» текущего пользователя.|  
|$PackageFolder$|Полный путь каталога, который содержит файлы сборки пакета для приложения.|  
|$ProgramFiles$|Значение переменной среды % ProgramFiles %.|  
|$RootFolder$|Полный путь к корневому каталогу приложения.|  
|$RootKey$|Корневой раздел реестра для приложения. По умолчанию используется корень HKEY_CURRENT_USER\Software\\*CompanyName*\\*ProjectName*\\*Номер_версии* (когда приложения, _Config добавляется к этому ключу). Задается значение RegistryRoot *имя_решения*pkgdef-файл.<br /><br /> Строка $RootKey$ может использоваться для извлечения значения реестра в подразделе приложения. Например, строка «$= $RootKey$ \AppIcon$» вернет значение записи AppIcon подраздел корневого приложения.<br /><br /> Средство синтаксического анализа последовательно обрабатывает pkgdef-файл и доступ к записи реестра в подраздел приложения только в том случае, если операция было определено ранее|  
|$ShellFolder$|Полный путь расположения, где установлен Visual Studio.|  
|$System$|В папку Windows\System32.|  
|$WINDIR$|Папка Windows.|  
  
 Если средство синтаксического анализа не распознает строку подстановки, или он не может определить значение записи реестра или переменную среды, то он не выполняет замену эту часть строки.