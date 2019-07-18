---
title: Перечисление DOCUMENTNAMETYPE | Документация Майкрософт
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
ms.openlocfilehash: 5ee258602c47951f4731dc1378542cc83d57d72b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955223"
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
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|Возвращает имя, как оно отображается в дереве приложения.|  
|DOCUMENTNAMETYPE_TITLE|Возвращает имя, как оно отображается в строке заголовка средства просмотра.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Возвращает имя файла без пути.|  
|DOCUMENTNAMETYPE_URL|Получает URL-адрес документа.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Получает заголовок, дополненный перечисления для идентификации.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)