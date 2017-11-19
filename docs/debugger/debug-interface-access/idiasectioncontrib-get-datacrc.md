---
title: "IDiaSectionContrib::get_dataCrc | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSectionContrib::get_dataCrc method
ms.assetid: 33b7488f-dc9c-47b3-b08c-737e0eb1bf7d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e99a55c5e74e707b94a3632226905d562156757f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasectioncontribgetdatacrc"></a>IDiaSectionContrib::get_dataCrc
Извлекает циклическую проверку избыточности (CRC) в разделе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_dataCrc (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает контрольную СУММУ данных в разделе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)