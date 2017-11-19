---
title: "IActiveScriptAuthor::IsCommitChar | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.IsCommitChar
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::IsCommitChar
ms.assetid: 7857c6f9-61e6-41e5-8e01-f56588c10421
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67dcdd7107372ee2766d59374a1d5aa9eb98576d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoriscommitchar"></a>IActiveScriptAuthor::IsCommitChar
Возвращает значение, указывающее, должны ли определенный символ запускать фиксации завершения инструкции для приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT IsCommitChar(  
   OLECHAR    ch,  
   BOOL       *pfcommit  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ch`  
 [in] Проверяемый символ.  
  
 `pfcommit`  
 [out] `True` при фиксации символ знаком; в противном случае — `False`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)