---
title: "Text_document_array — структура | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: TEXT_DOCUMENT_ARRAY Structure
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 03ed7f13b4e57f9e44ca147810614f980b24b9a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="textdocumentarray-structure"></a>TEXT_DOCUMENT_ARRAY — структура
Массив [интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md) объектов. С CoTaskMemAlloc выделенных элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef struct tagTEXT_DOCUMENT_ARRAY{    DWORD dwCount;    [size_is(dwCount)] IDebugDocumentText **Members;} TEXT_DOCUMENT_ARRAY;  
```  
  
## <a name="members"></a>Члены  
 `dwCount`  
 Число документов.  
  
 `Members`  
 Набор документов.  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)