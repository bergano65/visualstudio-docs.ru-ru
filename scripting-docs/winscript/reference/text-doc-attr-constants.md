---
title: Константы TEXT_DOC_ATTR | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 130895e0e70b1044fab5d5ab406f940b036c37f0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734254"
---
# <a name="textdocattr-constants"></a>Константы TEXT_DOC_ATTR
Описывают атрибуты документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>Константы  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|Документ доступен только для чтения.|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|Документ является первичным файлом этого дерева документов.|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|Этот документ является работника.|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|Документ представляет собой файл сценария.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)