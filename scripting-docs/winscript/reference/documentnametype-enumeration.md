---
title: Перечисление ДОКУМЕНТНАМЕТИПЕ | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 401eb759523ed1a33d24c3a298db0b3de2b7d5a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575878"
---
# <a name="documentnametype-enumeration"></a>Перечисление DOCUMENTNAMETYPE
Описывает тип, получаемый для документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
|DOCUMENTNAMETYPE_APPNODE|Возвращает имя, которое отображается в дереве приложения.|  
|DOCUMENTNAMETYPE_TITLE|Получает имя, отображаемое в заголовке окна средства просмотра.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Возвращает имя файла без пути.|  
|DOCUMENTNAMETYPE_URL|Возвращает URL-адрес документа.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Возвращает заголовок, добавленный с перечислением для идентификации.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)