---
title: IDiaSession::findInlineeLines | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: b6822d8b-70d5-470b-8278-3aec4680326c
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6603186fd35b1bc2a1ba4ccf2bf5ce052e3d6d65
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68165661"
---
# <a name="idiasessionfindinlineelines"></a>IDiaSession::findInlineeLines
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает перечисление, которое позволяет клиенту для выполнения итерации по информация о номере строки всех функций, которые являются встроенными, напрямую или косвенно, символ из указанного родительского объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findInlineeLines (   
   IDiaSymbol*       parent,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `parent`  
 [in] `IDiaSymbol` Объект, представляющий родительский объект.  
  
 `ppResult`  
 [out] Содержит `IDiaEnumLineNumbers` , содержащий список номеров строк, возвращаемых.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
