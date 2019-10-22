---
title: 'IDebugDocumentHelper:: Жетскриптблоккинфо | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.GetScriptBlockInfo
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::GetScriptBlockInfo
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a92aa00d7997ceccc583c88a070f6fbc7d4359d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576099"
---
# <a name="idebugdocumenthelpergetscriptblockinfo"></a>IDebugDocumentHelper::GetScriptBlockInfo
Извлекает диапазон символов и обработчик скриптов, соответствующий блоку скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwSourceContext`  
 окне Контекст источника для блока скрипта.  
  
 `ppasd`  
 заполняет Обработчик скриптов для этого блока сценария.  
  
 `piCharPos`  
 заполняет Расположение начала блока скрипта.  
  
 `cChars`  
 заполняет Число символов в блоке скрипта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод извлекает диапазон символов и обработчик скриптов, соответствующий блоку скрипта.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)