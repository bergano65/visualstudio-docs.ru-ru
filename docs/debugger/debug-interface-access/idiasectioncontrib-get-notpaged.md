---
title: IDiaSectionContrib::get_notPaged | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_notPaged method
ms.assetid: bb6baa40-fece-4a4c-aba9-f4b41f418f8b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0d02451343aad3cd08f618249aaf50a01f8b6f0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069217"
---
# <a name="idiasectioncontribgetnotpaged"></a>IDiaSectionContrib::get_notPaged
Получает флаг, указывающий, может ли быть оповещен разделе не хватает памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_notPaged (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out, retval] Возвращает `TRUE` Если раздел может быть оповещен; в противном случае — значение, возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)