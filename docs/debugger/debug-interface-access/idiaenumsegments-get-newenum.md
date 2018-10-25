---
title: IDiaEnumSegments::get__NewEnum | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::get__NewEnum method
ms.assetid: 504505fa-b35c-402f-a440-8972c589cc5b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3fb9d165fa0b9ee023ba6e9fdc0c4e3e9ab575f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818865"
---
# <a name="idiaenumsegmentsgetnewenum"></a>IDiaEnumSegments::get__NewEnum
Извлекает <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> версии этот перечислитель.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pRetVal  
 [out] Возвращает `IUnknown` интерфейс, который представляет <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> версии этот перечислитель.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)