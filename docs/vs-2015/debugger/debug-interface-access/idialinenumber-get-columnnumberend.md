---
title: IDiaLineNumber::get_columnNumberEnd | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d6fb8cb5b3cfa7aa741db4e49dc7c2b3e1daee4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192345"
---
# <a name="idialinenumbergetcolumnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает номер столбца источника от единицы, которой заканчивается выражения или оператора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_columnNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает номер столбца, в которой заканчивается выражения или оператора. Если значение равно нулю, сведения о столбце окончания отсутствует.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Значение столбца, возвращаемого этим методом является байтовое смещение в строку в позицию после последнего символа в строке инструкции.  
  
## <a name="see-also"></a>См. также  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
