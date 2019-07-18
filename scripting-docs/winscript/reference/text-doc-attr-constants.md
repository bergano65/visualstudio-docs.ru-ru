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
ms.openlocfilehash: d22b178d85d304f19e52727ef2c67d77f16da1b3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840087"
---
# <a name="textdocattr-constants"></a>Константы TEXT_DOC_ATTR
Описывают атрибуты документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>Константы  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|Документ доступен только для чтения.|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|Документ является первичным файлом этого дерева документа.|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|Документ является работника.|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|Документ представляет собой файл сценария.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)