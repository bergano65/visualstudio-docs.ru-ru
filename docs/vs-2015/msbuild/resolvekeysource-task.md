---
title: Задача ResolveKeySource | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd5cbe2f4998ab78ce39cde4b26a38b13c70b2f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193719"
---
# <a name="resolvekeysource-task"></a>Задача ResolveKeySource
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет источник ключа строгого имени.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `ResolveKeySource`.  
  
|Параметр|Description|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|Необязательный параметр `Int32`.<br /><br /> Возвращает или задает длительность (в секундах) отображения сообщения с обратным отсчетом.|  
|`AutoClosePasswordPromptTimeout`|Необязательный параметр `Int32`.<br /><br /> Получает или задает интервал времени в секундах перед закрытием диалогового окна запроса пароля.|  
|`CertificateFile`|Необязательный параметр `String`.<br /><br /> Возвращает или задает путь к файлу сертификата.|  
|`CertificateThumbprint`|Необязательный параметр `String`.<br /><br /> Возвращает или задает отпечаток сертификата.|  
|`KeyFile`|Необязательный параметр `String`.<br /><br /> Возвращает или задает путь к файлу ключа.|  
|`ResolvedKeyContainer`|Необязательный выходной параметр `String`.<br /><br /> Получает или задает разрешенный контейнер ключа.|  
|`ResolvedKeyFile`|Необязательный выходной параметр `String`.<br /><br /> Получает или задает разрешенный файл ключа.|  
|`ResolvedThumbprint`|Необязательный выходной параметр `String`.<br /><br /> Возвращает или задает отпечаток разрешенного сертификата.|  
|`ShowImportDialogDespitePreviousFailures`|Необязательный параметр `Boolean`.<br /><br /> Если задано значение `true`, нужно отображать диалоговое окно импорта, несмотря на предыдущие сбои.|  
|`SuppressAutoClosePasswordPrompt`|Необязательный параметр `Boolean`.<br /><br /> Получает или задает логическое значение, указывающее, закрывается ли диалоговое окно запроса пароля автоматически.|  
  
## <a name="remarks"></a>Remarks  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описание см. в разделе [базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также:  
 [Операции](../msbuild/msbuild-tasks.md)   
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)
