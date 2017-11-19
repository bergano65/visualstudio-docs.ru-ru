---
title: "IDiaStackWalkHelper::put_registerValue | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8abfd209e5c2f59a0c55128eb235fda868f4bfd5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalkhelperputregistervalue"></a>IDiaStackWalkHelper::put_registerValue
Задает значение регистра.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `index`  
 [in] Значение из [CV_HREG_e-перечисление](../../debugger/debug-interface-access/cv-hreg-e.md) перечисление, определяющее регистра для записи.  
  
 `NewVal`  
 [in] Новое значение регистра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Несмотря на размер значения реализация следует хранить только регистр обычно содержат. Например 8-битный регистр будет содержать только младшие 8-битов заданного значения.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)