---
title: 'IDebugApplicationNode100:: Жетексклудеддокументс | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::GetExcludedDocuments
ms.assetid: d44583a7-0b0b-4799-b075-837ad1da1946
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c135aa85ca65a44f6f970e83d7975bb441ff56f5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574756"
---
# <a name="idebugapplicationnode100getexcludeddocuments"></a>IDebugApplicationNode100::GetExcludedDocuments
Возвращает текстовые документы, скрытые указанным фильтром.  
  
> [!IMPORTANT]
> [Интерфейс IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) реализуется с помощью PDM v 10.0 и более поздних версий. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetExcludedDocuments(        [in] APPLICATION_NODE_EVENT_FILTER filter,        [out] TEXT_DOCUMENT_ARRAY* pDocuments        );  
```  
  
#### <a name="parameters"></a>Параметры  
 `filter`  
 Фильтр.  
  
 `pDocuments`  
 Набор документов.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)