---
title: IDiaSymbol::findInlineeLinesByAddr | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: f1ab47ca-c851-48ea-9c12-47fb80b31102
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b07c45fc72f225b29b9850ffb1c9b38d6240760
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823873"
---
# <a name="idiasymbolfindinlineelinesbyaddr"></a>IDiaSymbol::findInlineeLinesByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает перечисление, которое позволяет клиенту для выполнения итерации по информация о номере строки всех функций, которые являются встроенными, напрямую или косвенно, в этот символ в указанный диапазон адресов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findInlineeLinesByAddr (   
   DWORD                 isect,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `isect`  
 [in] Задает компонент прокрутки на разделе адреса.  
  
 `offset`  
 [in] Задает компонент прокрутки на смещения адреса.  
  
 `length`  
 [in] Указывает диапазон адресов, в байтах, чтобы охватить с этим запросом.  
  
 `ppResult`  
 [out] Содержит `IDiaEnumLineNumbers` , содержащий список номеров строк, возвращаемых.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)



