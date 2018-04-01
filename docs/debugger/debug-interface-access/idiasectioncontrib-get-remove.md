---
title: IDiaSectionContrib::get_remove | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_remove method
ms.assetid: fd30ab7b-022b-4402-a42a-2d38e274c1b1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cb03830b5076a39f06e4fa4a9fe8a867f1131771
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiasectioncontribgetremove"></a>IDiaSectionContrib::get_remove
Возвращает флаг, указывающий, удален ли раздел, прежде чем оно станет изображением в памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_remove (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает `TRUE` Если раздел не для добавления изображения в памяти; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)