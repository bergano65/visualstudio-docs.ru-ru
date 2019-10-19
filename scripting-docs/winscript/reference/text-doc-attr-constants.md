---
title: Константы TEXT_DOC_ATTR | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- TEXT_DOC_ATTR
apilocation:
- scrobj.dll
helpviewer_keywords:
- TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3604c06b6cb36cc4ff7ef6c76348b5ece53bed61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572985"
---
# <a name="text_doc_attr-constants"></a>Константы TEXT_DOC_ATTR
Описывают атрибуты документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>Константы  
  
|Константа|значения|Описание|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|Документ доступен только для чтения.|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|Документ является первичным файлом этого дерева документов.|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|Документ является рабочим.|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|Документ является файлом скрипта.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)