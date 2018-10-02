---
title: Задача VCMessage | Документы Майкрософт
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
manager: ghogen
ms.openlocfilehash: d667c53e00e7b92d133c260b5c3cc471a64f355b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562188"
---
# <a name="vcmessage-task"></a>Задача VCMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [vcmessage-задача](https://docs.microsoft.com/visualstudio/msbuild/vcmessage-task).  
  
  
Заносит в журнал предупреждения и сообщения об ошибках, возникшие при сборке.  
  
## <a name="remarks"></a>Примечания  
 Эта задача помогает реализовать MSBuild для Visual C++ и не предназначена для вызова пользователем. Дополнительные сведения см. в разделе <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры задачи **VCMessage**.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|**Аргументы**|Необязательный параметр типа **String**.<br /><br /> Разделенный точками с запятой список отображаемых сообщений.|  
|**Код**|Обязательный параметр **string**.<br /><br /> Номер ошибки, определяющий сообщение.|  
|**Type**|Необязательный параметр типа **String**.<br /><br /> Задает тип выдаваемого сообщения. Укажите `"Warning"`, чтобы выдать предупреждающее сообщение, или `"Error"`, чтобы выдать сообщение об ошибке.|  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



