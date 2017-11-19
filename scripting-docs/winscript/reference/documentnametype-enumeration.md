---
title: "Перечисление DOCUMENTNAMETYPE | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DOCUMENTNAMETYPE
apilocation: scrobj.dll
helpviewer_keywords: DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0bd21dddd209f21ae64ea2775bbaa0da226f077
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="documentnametype-enumeration"></a>Перечисление DOCUMENTNAMETYPE
Описывает тип, получаемый для документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|Возвращает имя, как оно отображается в дереве приложения.|  
|DOCUMENTNAMETYPE_TITLE|Возвращает имя, которое отображается в строке заголовка средства просмотра.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Возвращает имя файла без пути.|  
|DOCUMENTNAMETYPE_URL|Получает URL-адрес документа.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Возвращает название, дополненная перечисления для идентификации.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)