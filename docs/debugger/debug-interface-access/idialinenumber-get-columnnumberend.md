---
title: "IDiaLineNumber::get_columnNumberEnd | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 04894f9ef6d1779b5e27c2552b5ea05d84649a2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idialinenumbergetcolumnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
Извлекает один исходный номер столбца, где заканчивается выражения или оператора.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_columnNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает номер столбца, в которой заканчивается выражения или оператора. Если значение равно нулю, сведения о столбцах окончания отсутствует.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Значение столбца, возвращаемого этим методом является байт смещение в строке на позицию после последнего символа в строке инструкции.  
  
## <a name="see-also"></a>См. также  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)