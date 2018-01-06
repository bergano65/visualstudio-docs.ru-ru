---
title: "IDiaStackWalkHelper::pdataForVA | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 251b54ca712078e5252a4a55c9237545e14a7536
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Возвращает PDATA блок данных, связанных с виртуальный адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `va`  
 [in] Указывает виртуальный адрес для получения данных.  
  
 `cbData`  
 [in] Размер в байтах для получения данных.  
  
 `pcbData`  
 [out] Возвращает фактический размер данных в байтах, который был получен.  
  
 `pbData`  
 [in, out] Буфер, заполнено запрошенные данные. Не может быть `NULL`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если нет PDATA по указанному адресу. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 (Раздел с именем «.pdata») PDATA компилируемого объекта содержит сведения об обработке исключений для функции.  
  
 Вызывающий объект знает, какой объем данных должны быть возвращены, вызывающий оператор имеет не нужно запрашивать объему данных доступен. Таким образом, он допустим для реализации этого метода будут возвращать ошибку, если `pbData` параметр `NULL`.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)