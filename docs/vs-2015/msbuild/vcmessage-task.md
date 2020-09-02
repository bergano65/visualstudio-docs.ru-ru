---
title: Задача VCMessage | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 508d1fe33046f6051c9c5c1b8e54036e78ae7d2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193351"
---
# <a name="vcmessage-task"></a>Задача VCMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Заносит в журнал предупреждения и сообщения об ошибках, возникшие при сборке.  
  
## <a name="remarks"></a>Remarks  
 Эта задача помогает реализовать MSBuild для Visual C++ и не предназначена для вызова пользователем. Дополнительные сведения см. в разделе <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры задачи **VCMessage**.  
  
|Параметр|Description|  
|---------------|-----------------|  
|**Аргументы**|Необязательный параметр **String** .<br /><br /> Разделенный точками с запятой список отображаемых сообщений.|  
|**Code**|Обязательный параметр **string**.<br /><br /> Номер ошибки, определяющий сообщение.|  
|**Тип**|Необязательный параметр **String** .<br /><br /> Задает тип выдаваемого сообщения. Укажите `"Warning"`, чтобы выдать предупреждающее сообщение, или `"Error"`, чтобы выдать сообщение об ошибке.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)
