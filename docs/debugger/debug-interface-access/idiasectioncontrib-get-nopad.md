---
title: "IDiaSectionContrib::get_nopad | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6bbabc5497e59db31535f87761bd081fe2eb0a6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasectioncontribgetnopad"></a>IDiaSectionContrib::get_nopad
Возвращает флаг, указывающий ли раздел не быть дополняются до следующей границы памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_nopad(  
   BOOL* pRetVal  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает `TRUE` Если разделе быть заполнено до следующего границы памяти; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Это свойство обычно используется только в старых файлов.  
  
## <a name="see-also"></a>См. также  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)