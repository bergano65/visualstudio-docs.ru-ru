---
title: Задача ResolveKeySource | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: a51b9b07be214a6713da4d9d6f9ccf99814b270f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570971"
---
# <a name="resolvekeysource-task"></a>Задача ResolveKeySource
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задача ResolveKeySource](https://docs.microsoft.com/visualstudio/msbuild/resolvekeysource-task).  
  
  
Определяет источник ключа строгого имени.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `ResolveKeySource`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|Необязательный параметр `Int32` .<br /><br /> Возвращает или задает длительность (в секундах) отображения сообщения с обратным отсчетом.|  
|`AutoClosePasswordPromptTimeout`|Необязательный параметр `Int32` .<br /><br /> Получает или задает интервал времени в секундах перед закрытием диалогового окна запроса пароля.|  
|`CertificateFile`|Необязательный параметр `String` .<br /><br /> Возвращает или задает путь к файлу сертификата.|  
|`CertificateThumbprint`|Необязательный параметр `String` .<br /><br /> Возвращает или задает отпечаток сертификата.|  
|`KeyFile`|Необязательный параметр `String` .<br /><br /> Возвращает или задает путь к файлу ключа.|  
|`ResolvedKeyContainer`|Необязательный выходной параметр `String`.<br /><br /> Получает или задает разрешенный контейнер ключа.|  
|`ResolvedKeyFile`|Необязательный выходной параметр `String`.<br /><br /> Получает или задает разрешенный файл ключа.|  
|`ResolvedThumbprint`|Необязательный выходной параметр `String`.<br /><br /> Возвращает или задает отпечаток разрешенного сертификата.|  
|`ShowImportDialogDespitePreviousFailures`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, нужно отображать диалоговое окно импорта, несмотря на предыдущие сбои.|  
|`SuppressAutoClosePasswordPrompt`|Необязательный параметр `Boolean` .<br /><br /> Получает или задает логическое значение, указывающее, закрывается ли диалоговое окно запроса пароля автоматически.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



