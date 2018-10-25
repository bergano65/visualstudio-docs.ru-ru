---
title: IDiaStackWalkHelper::symbolForVA | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9af63460d3b5c082f52d3dbd9725fbfeef9c24f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863923"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
Получает символ, который содержит указанный виртуальный адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `va`  
 [in] Виртуальный адрес, содержащийся в запрошенный символа. Символ должен быть `SymTagFunctionType` (значение из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисления).  
  
 `ppSymbol`  
 [out] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий символ по указанному адресу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)