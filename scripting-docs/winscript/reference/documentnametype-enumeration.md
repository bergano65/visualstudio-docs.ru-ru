---
title: Перечисление DOCUMENTNAMETYPE | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 31e304cfbb0ed7cd19b832d7ed7c33ccc2c930c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094774"
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
|DOCUMENTNAMETYPE_APPNODE|Возвращает имя, как оно отображается в дереве приложения.|  
|DOCUMENTNAMETYPE_TITLE|Возвращает имя, как оно отображается в строке заголовка средства просмотра.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Возвращает имя файла без пути.|  
|DOCUMENTNAMETYPE_URL|Получает URL-адрес документа.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Получает заголовок, дополненный перечисления для идентификации.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)