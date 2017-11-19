---
title: "IDiaSession::findInlineeLinesByVA | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0309dfd4f14ed7bdb049cdb0bde16a038bb78e37
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindinlineelinesbyva"></a>IDiaSession::findInlineeLinesByVA
Возвращает перечисление, которое позволяет клиенту итерации сведения о номерах строк для всех функций, которые являются встроенными, напрямую или косвенно, символ из указанного родительского объекта и содержащихся в указанный виртуальный адрес (VA).  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           parent,   ULONGLONG             va,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `parent`  
 [in] `IDiaSymbol` Объект, представляющий родительский объект.  
  
 `va`  
 [in] Указывает адрес как ва.  
  
 `length`  
 [in] Указывает диапазон адресов, в байтах, покрывающие с этим запросом.  
  
 `ppResult`  
 [out] Содержит `IDiaEnumLineNumbers` , содержащий список номеров строк, возвращаемых.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)