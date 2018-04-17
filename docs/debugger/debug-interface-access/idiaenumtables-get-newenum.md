---
title: IDiaEnumTables::get__NewEnum | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::get__NewEnum method
ms.assetid: 7b1159c7-a5f0-4baa-861a-dc11437d8b93
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a29c91159855901a2c2b0666b21830d7eac1d5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiaenumtablesgetnewenum"></a>IDiaEnumTables::get__NewEnum
Извлекает <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> версии этот перечислитель.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает `IUnknown` интерфейс, который представляет <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> версии этот перечислитель.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)